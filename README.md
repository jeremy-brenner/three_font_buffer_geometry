# three_font_buffer_geometry

This is a helper class for [Three.js](http://threejs.org) [TextGeometry](http://threejs.org/docs/#Reference/Extras.Geometries/TextGeometry).  It prebuilds and saves each character in a seperate [BufferGeometry](http://threejs.org/docs/#Reference/Core/BufferGeometry) and then builds a [Mesh](http://threejs.org/docs/#Reference/Objects/Mesh) for each letter combining them into a single [Object3D](http://threejs.org/docs/#Reference/Core/Object3D).  This avoids creating new geometries for every new string reusing the buffer geometries already created giving a noticeable performance boost. I wrote this to solve a major performance issue in my [jewel-clone game](https://github.com/jeremy-brenner/jewel-clone)

Usage: 

    var parameters = {
      size: 20,
      height: 10,
      curveSegments: 3,
      font: "droid sans",
      weight: "normal",
      style: "normal",
      bevelThickness: 10,
      bevelSize: 5,
      bevelEnabled: true,
      extrudeMaterial: 1
    }

    var material = new THREE.MeshBasicMaterial({color:'blue'})

    var buffer_font = new THREE.FontBufferGeometry(parameters)

    var mesh = buffer_font.buildMesh( 'The quick brown fox jumped over the lazy dog.', material )


The constructor for FontBufferGeometry takes an optional second parameter of a string of characters to prebuild geometries for.