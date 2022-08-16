# Tensorflow

[Install Tensorflow on M1 Mac](https://caffeinedev.medium.com/how-to-install-tensorflow-on-m1-mac-8e9b91d93706)

### Pipeline Config
Pipeline files are obtained from [Github tensorflow repository](https://github.com/tensorflow/models/blob/master/research/object_detection/samples/configs/ssd_mobilenet_v2_coco.config).  the object detection training pipeline must be configured. It defines which model and what parameters will be used for training. The pipeline file is edited to add the number of classes.

### Saved Model
Directory structure of a saved_model:

    -rw-r--r--  1 345018 89939   77 Mar 30  2018 checkpoint
    -rw-r--r--  1 345018 89939  67M Mar 30  2018 frozen_inference_graph.pb
    -rw-r--r--  1 345018 89939  65M Mar 30  2018 model.ckpt.data-00000-of-00001
    -rw-r--r--  1 345018 89939  15K Mar 30  2018 model.ckpt.index
    -rw-r--r--  1 345018 89939 3.4M Mar 30  2018 model.ckpt.meta
    -rw-r--r--  1 345018 89939 4.2K Mar 30  2018 pipeline.config
    drwxr-xr-x  3 345018 89939 4.0K Mar 30  2018 saved_model

TensorFlow graph proto. A checkpoint will typically consist of three files:

    model.ckpt-${CHECKPOINT_NUMBER}.data-00000-of-00001
    model.ckpt-${CHECKPOINT_NUMBER}.index
    model.ckpt-${CHECKPOINT_NUMBER}.meta

After export, you should see the directory ${EXPORT_DIR} containing the following:

- saved_model/, a directory containing the saved model format of the exported model
- frozen_inference_graph.pb, the frozen graph format of the exported model
- model.ckpt.*, the model checkpoints used for exporting
- checkpoint, a file specifying to restore included checkpoint files
- pipeline.config, pipeline config file for the exported model

### Label Map
You'll need a `.pbtxt` label map file, The label map tells the trainer what each object is by defining a mapping of class names to class ID numbers. example:

    item {
    name: "blueball",
    id: 1,
    display_name: "blueball"
    }
    item {
        name: "redball",
        id: 2,
        display_name: "redball"
    }

### Train Model
Train the model:

    python /content/models/research/object_detection/model_main.py \
    --pipeline_config_path={pipeline_fname} \
    --model_dir={model_dir} \
    --alsologtostderr \
    --num_train_steps={num_steps} \
    --num_eval_steps={num_eval_steps}




### Export Model
Now that training is complete, the last step is to generate the frozen inference graph (.pb file). The checkpoint at the highest number of steps will be used to generate the frozen inference graph.


    python /content/models/research/object_detection/export_inference_graph.py \
    --input_type=image_tensor \
    --pipeline_config_path={pipeline_fname} \
    --output_directory={output_directory} \
    --trained_checkpoint_prefix={last_model_path}

The `.pb` file contains the object detection classifier.

To get the frozen graph, run the export_tflite_ssd_graph.py script from the `models/research` directory with this command:

    export CONFIG_FILE=PATH_TO_BE_CONFIGURED/pipeline.config
    export CHECKPOINT_PATH=PATH_TO_BE_CONFIGURED/model.ckpt
    export OUTPUT_DIR=/tmp/tflite

    object_detection/export_tflite_ssd_graph.py \
    --pipeline_config_path=$CONFIG_FILE \
    --trained_checkpoint_prefix=$CHECKPOINT_PATH \
    --output_directory=$OUTPUT_DIR \
    --add_postprocessing_op=true

Make sure not to confuse `export_tflite_ssd_graph` with `export_inference_graph` in the same directory. Both scripts output frozen graphs: `export_tflite_ssd_graph` will output the frozen graph that we can input to TensorFlow Lite directly and is the one we’ll be using.    

`Rapid-React-mnet.tflite` output is `output_boxes`

`model.tflite` output is `StatefulPartitionedCall` which is a TF2 model

## References

- [Running on mobile with TensorFlow Lite](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/running_on_mobile_tensorflowlite.md)