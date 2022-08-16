# Node Package Manager

Install Node Package Manager.

    sudo apt install nodejs

If you want a newer version:

    curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -

    sudo apt install nodejs

Start a new project and get a `package.json`:

    npm init -y

Add typescript to project.  The `-D` means dependency:

    yarn add -D typescript

Add the typscript compiler:

    npx tsc --init  

Edit the package.json file to include the build script:

    "scripts": {
        "build": "tsc"
    },

Create a typescript file called `src/index.ts` and add the following line:

    console.log("Hello from typescript");

Compile the project.  This will create the nodejs file `src/index.js`:

    yarn build

Run the nodejs file:

    node src/index.js

### Compile and Run

    yarn add -D ts-node

Edit the package.json file:

    "scripts": {
        "start": "ts-node src/index.ts",
        "build": "tsc"
    },

To compile and run:

    yarn start

### Use Express and Install types

    yarn add express
    yarn add -D @types/express
    yarn add -D @types/node

### Notes

If you get the red squiggle error lines you may have to restart the server.  Bring up the command pallet
## References
