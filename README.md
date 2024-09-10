
# A simple html Three.js Cube

This is a simple example of a 3D cube rotating using [Three.js](https://threejs.org/), a popular 3D graphics library for the web.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Code Overview](#code-overview)
- [License](#license)

## Installation

To use this example, you will need to set up a local development environment.

1. Clone this repository or download the files.
2. Create an `index.html` and `main.js` file with the provided code below.

### index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>My first three.js app</title>
    <style>
      * { margin: 0; padding: 0; box-sizing: border-box; }
    </style>
  </head>
  <body>
    <script type="importmap">
      {
        "imports": {
          "three": "https://cdn.jsdelivr.net/npm/three@0.167.1/build/three.module.js",
          "three/addons/": "https://cdn.jsdelivr.net/npm/three@0.167.1/examples/jsm/"
        }
      }
    </script>
    <script type="module" src="main.js"></script>
  </body>
</html>
```

### main.js

```javascript
import * as THREE from 'three';

// Scene
const scene = new THREE.Scene();
scene.background = new THREE.Color('#F0F0F0');

// Camera
const camera = new THREE.PerspectiveCamera(40, window.innerWidth / window.innerHeight, 0.1, 1000);
camera.position.z = 5;

// Object
const geometry = new THREE.BoxGeometry(); 
const material = new THREE.MeshLambertMaterial({ color: '#800080', emissive: '#4B0082' });

const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

// Lighting
const light = new THREE.DirectionalLight(0x9CDB86, 10);
light.position.set(1, 1, 1);
scene.add(light);

// Renderer
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight); 
document.body.appendChild(renderer.domElement);

// Animate
function animate() {
    requestAnimationFrame(animate);
    cube.rotation.x += 0.010;
    cube.rotation.y += 0.010;
    
    renderer.render(scene, camera);
}

animate();
```

## Usage

Open `index.html` in your browser to see the rotating cube in action.

