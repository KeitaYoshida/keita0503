<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <div class="column">
      <button class="button" @click="cameraStart">カメラスタート</button>
    </div>
    <video autoplay></video>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  components: {
    HelloWorld
  },
  methods: {
    cameraStart() {
      const p = navigator.mediaDevices.getUserMedia({
        audio: false,
        video: {
          width: this.width,
          height: this.height,
          frameRate: { ideal: 5, max: 15 }
        }
      });
      p.then(function(mediaStream) {
        document.querySelector("video").srcObject = mediaStream;
      });
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
