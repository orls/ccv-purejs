#Face detection js

A fork of the [pure-javascript face detection](https://github.com/liuliu/ccv/tree/current/js) in [Liu Liu's CCV library](https://github.com/liuliu/ccv) (in branch 'current'), converted for Node and npm.

# Usage

This package provides the method `detect_objects`, to which you pass a parameters hash. The most important parameter is the canvas obj, into which you should have already loaded an image.

This method returns an array of hashes, each representing a face, with the following fields:

* `x`, `y` : the coordinates of the top-left corner of the face's bounding box
* `width`, `height` : the pixel dimensions of the face's bounding box
* `neighbours`, `confidence` : info from the detection algorithm

### Simple example

    var face_detect = require('face_detect'),
        Canvas = require('canvas');
    
    // ... initialize a canvas object ...
    
    var result = face_detect.detect_objects({ "canvas" : myCanvas,
      "interval" : 5,
      "min_neighbors" : 1 });
    
    console.log('Found ' + result.length  + ' faces.');
    
    for (var i = 0; i < result.length; i++){
      var face =  result[i];
      console.log(face);
    }
    

in future, directly passing an image path or a buffer containing raw png data will be supported

# Install

This project is installed with [npm](http://npmjs.org).

## from npm repository
  
    $ npm install face-detect

## locally with npm

    $ git clone https://orls@github.com/orls/ccv-purejs.git face-detect
    $ cd face-detect
    $ npm install
    $ cd ../my-project
    $ npm install ../face-detect
