<template>
  <div class="section">
    <div id="three" />
    <button class="btn1" @click.prevent="addPoint">start</button>
  </div>
</template>
<script>
import * as THREE from "three";
import { Scene } from "./components/scene";

let scene;

export default {
  name: "ThreeScene",
  mounted() {
    const width = window.innerWidth;
    const height = window.innerHeight;
    console.log(width, height);
    scene = Scene();
    scene.init({ canvasId: "three", width, height });
  },
  methods: {
    addPoint() {
      scene.setOrbitCont();
      scene.addPoint({
        radius: 5,
        segments: 32,
        position: new THREE.Vector3(0.0, 0.0, 0.0),
      });
    },
  },
};
</script>
<style scoped>
#three {
  width: 100vw;
  height: 100vh;
  /* border: 10px solid red; */
  box-sizing: border-box;
}

.section {
  position: relative;
}

.btn1 {
  position: absolute;
  top: 100px;
  left: 50%;
  z-index: 99;
}

.btn2 {
  position: absolute;
  bottom: 100px;
  left: 50%;
  z-index: 99;
}
</style>
