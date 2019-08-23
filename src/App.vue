<template>
  <div id="app">
    <header>
      <h1>NOAA-16</h1>
      <h2>Weather Satellite Data</h2>
    </header>
    <main class="video-container">
      <VideoPanel
        v-for="n in testNum"
        videoSrc="http://52.54.73.208/temp.mp4"
        :videoId="n"
        :key="n"
      />
    </main>
  </div>
</template>

<script>
import VideoPanel from "./components/VideoPanel.vue";

export default {
  name: "app",
  components: {
    VideoPanel
  },
  data () {
    return {
      testNum: [1, 2, 3]
    }
  },
  methods: {

  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.video-container {
  display: flex;
  align-content: center;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
