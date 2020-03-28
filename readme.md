# ESM Wavefront OBJ 3D model file format parser

This library is an ESM module for parsing Wavefront OBJ files into a JavaScript
structure suitable for further processing or rendering.

## Status

This library is not really maintained.

It can parse edges and faces, but ignores the other commands and throws on some
I haven't set to be ignored yet. I don't know if I will develop it further to
handle this better.

## Installation

```js
import parse from 'https://tomashubelbauer.github.io/esm-obj/index.js';
```

## Usage

```js
const mesh = parse(text);
```

The return values is an object with the following shape:

- `minX` is the smallest X coordinate value of any vertex found
- `maxX` is the largest X coordinate value of any vertex found
- `minY` is the smallest Y coordinate value of any vertex found
- `maxY` is the largest Y coordinate value of any vertex found
- `minZ` is the smallest Z coordinate value of any vertex found
- `maxZ` is the largest Z coordinate value of any vertex found
- `shapes` is an array of objects, one of:
  - Edge:
    - `type` is `edge`
    - `from` is the 'from' vertex - an array of X, Y, Z coordinate values
    - `to` is the 'to' vertex - an array of X, Y, Z coordinate values
  - Face:
    - `type` is `face`
    - `points` is an array of vertices that connect up to form the face polygon
      - The loop of the vertices is not closed (first != last)
      - The points are represented using an array of X, Y, Z coordinate values

## To-Do

### Add the promised support for edge parsing

### Add a test comprising of various OBJ files and their JSON representations

### Consider adding support for more advanced OBJ shapes

### Consider adding support for textures
