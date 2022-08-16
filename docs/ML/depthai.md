# Depthai & OpenVino

Depthai install files:

`~/depthai`

>`resources/nn` contain the model json files.  When these run they download the blobs into: `~/.cache/blobconverter/`

![Romi Install](../images/DeploymentNotes/DeploymentNotes.004.jpeg)

## Converting to Blob

Use the [Online Blob Converter](http://blobconverter.luxonis.com)

Or install locally:

    python3 -m pip install -U blobconverter

To convert:

    python3 -m blobconverter --openvino-xml /path/to/custom_model.xml --openvino-bin /path/to/custom_model.bin

## Install DepthAI on M1 Mac
Create a conda environment:

    conda create --name DepthAIEnv39 python=3.9
    conda activate DepthAIEnv39

Install depthAI software:

    python3 -m pip install -U pip
    brew update
    brew install cmake libusb
    cd ~; mkdir DepthAI; cd DepthAI
    git clone --recursive  https://github.com/luxonis/depthai-python.git
    cd depthai-python

Checkout the M1 branch:

    git checkout mac_arm64_wheels
    python3 examples/install_requirements.py

Run the example:

    python3 examples/ColorCamera/rgb_preview.py

## References
- [Depthai Documentation](https://docs.luxonis.com/en/latest/)
- [OpenVino Notebooks](https://github.com/openvinotoolkit/openvino_notebooks)

- [OpenVINO Tutorial](https://www.youtube.com/watch?v=HEntm0TUqM8&list=PLg-UKERBljNxdIQir1wrirZJ50yTp4eHv&index=20&ab_channel=IntelSoftware) - YouTube

## Errors
-- Configuring incomplete, errors occurred!
See also "/Users/martinwhite/DepthAI/depthai-python/build/CMakeFiles/CMakeOutput.log".
See also "/Users/martinwhite/DepthAI/depthai-python/build/CMakeFiles/CMakeError.log".