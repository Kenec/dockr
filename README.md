# dockr

[![Build Status](https://travis-ci.org/Kenec/dockr.svg?branch=develop)](https://travis-ci.org/Kenec/dockr)
[![Coverage Status](https://coveralls.io/repos/github/Kenec/dockr/badge.svg?branch=master)](https://coveralls.io/github/Kenec/dockr?branch=master)
<br>
**dockr** is an an NPM package for auto generating Dockerfile, building docker image, running and stopping the docker container in Node.js. 

## Installation
```
npm install dockr --save-dev
```

## Configuration
1. Setup the dockr config file in your application ***package.json*** file
```
...

"dockr":{
    "cmd": "node index.js",
    "expose": 3000,
    "env": [
        { "name": "name 1" },
        { "metadata": "meta data 1" },
        { "path": "Log Path 1" }
      ],
    "label": [
        { "version": "1.0" }, 
        { "description": "A sample label" },
        { "maintainer": "nnamani.kenechukwu@gmail.com" }
      ],
    "workdir": "/app"
  },
```

2. Add script to generate Dockerfile, build docker image, start and stop docker container in your ***scripts*** section of ***package.json*** file
```
....

"scripts": {
    "start": "node index.js",
    "dockr-generate": "node ./node_modules/dockr generate",
    "dockr-build": "node ./node_modules/dockr build",
    "dockr-run": "node ./node_modules/dockr run",
    "dockr-stop": "node ./node_modules/dockr stop"
  },
```

Alternatively, we can use *dockr* aliases such as
```
....

"scripts": {
    "start": "node index.js",
    "dockr-generate": "node ./node_modules/dockr g",
    "dockr-build": "node ./node_modules/dockr b",
    "dockr-run": "node ./node_modules/dockr r",
    "dockr-stop": "node ./node_modules/dockr s"
  },
```

### Usage
1. To generate Dockerfile for your application, run
```
npm run dockr-generate
```

2. To build docker image using the generated Dockerfile, run
```
npm run dockr-build
```

3. To run the docker container using the built image, run
```
npm run dockr-run
```
***Visit the application on your web browser on `http://localhost:<port number>/`***

4. To stop the docker container, run
```
npm run dockr-stop
```

### dockr config commands
| Commands      | Description                                                       | Type                | Required  |
| ------------- |:------------------------------------------------------------------|:--------------------| :---------|
| **cmd**       | Command that docker will use to start your application            | String              | **True**  |
| **expose**    | The application port which you want the container to run on       | Integer             | **True**  |
| **env**       | The environment variables for docker                              | Array of Objects    | **False** |
| **label**     | Key value pair of metadata to the image                           | Array of Objects    | **False** |
| **workdir**   | The working directory in the Dockerfile                           | String              | **False** |


### ISSUES
To report an issue or give feedback, Click link
[Issues and Feedback](https://github.com/Kenec/dockr/issues)

### Contributing
We are more than happy to have you contribute to this project.

### License
[MIT](https://github.com/Kenec/dockr/blob/master/LICENSE)
