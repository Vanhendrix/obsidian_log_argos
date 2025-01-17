---
{"dg-publish":true,"permalink":"/templates/test/","title":"test","tags":["log"],"created":"2025-01-15","updated":"2025-01-15"}
---

<iframe style="display: block; margin-left: auto; margin-right: auto;" src="https://drive.google.com/file/d/1iidiH2A1tmqAow24-6YcfKrxvHd56ON8/preview" width="640" height="346" allow="autoplay">
</iframe>
<br>
<iframe style="display: block; margin-left: auto; margin-right: auto;" src="https://drive.google.com/file/d/10Y3Vts8bztgPf7xSpkFZKEjdIYuT72dL/preview" width="540" height="540" allow="autoplay"></iframe>
<br>

<div id="threejs-viewer" style="width: 100%; height: 500px;"></div>

<script type="module">
  import * as THREE from 'https://cdn.jsdelivr.net/npm/three@0.158.0/build/three.module.js';
  import { OrbitControls } from 'https://cdn.jsdelivr.net/npm/three@0.158.0/examples/jsm/controls/OrbitControls.js';

  document.addEventListener('DOMContentLoaded', () => {
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    camera.position.set(0, 5, 10);

    const renderer = new THREE.WebGLRenderer({ antialias: true });
    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setPixelRatio(window.devicePixelRatio);
    document.getElementById('threejs-viewer').appendChild(renderer.domElement);

    // Lumières
    const light = new THREE.DirectionalLight(0xffffff, 1);
    light.position.set(10, 10, 10);
    scene.add(light);

    // Cube
    const geometry = new THREE.BoxGeometry();
    const material = new THREE.MeshStandardMaterial({ color: 0x00ff00 });
    const cube = new THREE.Mesh(geometry, material);
    scene.add(cube);

    // Animation : rotation du cube
    const animate = () => {
      requestAnimationFrame(animate);
      cube.rotation.x += 0.01;
      cube.rotation.y += 0.01;
      renderer.render(scene, camera);
    };
    animate();

    // Contrôles utilisateur
    const controls = new OrbitControls(camera, renderer.domElement);
    controls.target.set(0, 0, 0);
    controls.update();

    // Redimensionner
    window.addEventListener('resize', () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    });
  });
</script>


