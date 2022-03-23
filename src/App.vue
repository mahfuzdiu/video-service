<template>
  <div>
    <div>
      <img id="image" :src="imgSrc" height="200" width="200"/>
      <video id="video" :src="videoSrc" height="200" width="200"> </video>
        <canvas id="canvas" height="200" width="200"></canvas>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import etro from "etro"

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data(){
    return {
      videoSrc :  require("./assets/video1.mp4"),
      imgSrc : require("./assets/logo.png")
    }
  },
  mounted(){
    // (function a() {
      var outputCanvas = document.getElementById("canvas")
      var imgSrcHtml = document.getElementById("image")
      var videoSrcHtml = document.getElementById("video")
      
      var movie = new etro.Movie({ canvas: outputCanvas })
      movie.width = 200  // also sets the canvas's width to 200
      movie.height = 200

      var imageLayer = new etro.layer.Image({ startTime: 0, duration: 2, source: imgSrcHtml })
      movie.addLayer(imageLayer)

      var textLayer = new etro.layer.Text({ startTime: 1, duration: 2, text: "Wp plugin render test" })
      movie.addLayer(textLayer)

      var videoLayer = new etro.layer.Video({ startTime: 2, duration: 2, source: videoSrcHtml })
      movie.addLayer(videoLayer)
      movie.play()
      // movie.record({ frameRate: 24, duration: 3, video: true })  // or just `play` if you don't need to save it
      // .then(blob => {
      //   console.log(blob)
      // })

//       var audioLayer = new etro.layer.Audio({ startTime: 2, duration: 8, source: this.videoSrc })
// movie.addLayer(audioLayer)

// })();
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
</style>
