<template>
  <div id="app">
    <Camera v-on:take-picture="this.takePicture"/>
    <Gallery/>
  </div>
</template>

<script>
import Camera from './components/Camera';
import Gallery from './components/Gallery';

export default {
 name: 'App',
	components: {
    Camera,
    Gallery
  },
	methods: {
    takePicture: () => {
      console.log("Take Picture start...");

      let ratio = (window.innerHeight < window.innerWidth) ? 16/9 : 9/16;

      const picture = document.querySelector("canvas");
      picture.width = (window.innerWidth < 1280) ? window.innerWidth : 1280;
      picture.height = window.innerWidth / ratio;

      const ctx = picture.getContext("2d");
      ctx.imageSmoothingEnabled = true;
      ctx.imageSmoothingQuality = "high";
      ctx.drawImage(document.querySelector("video"), 0, 0, picture.width, picture.height);

      console.log("Take Picture done...");

    }
	}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* 
video {
	width: 100%;
	background: rgba(0, 0, 0, 0.2);
} */

</style>
