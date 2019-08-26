<template>
  <div id="app">
    <header>
      <h1>NOAA-16</h1>
      <h2>Weather Satellite Data</h2>
    </header>
    <main class="video-container">
      <VideoPanel
        ref="videoPanel"
        v-for="video in videos"
        :videoSrc="video.source"
        :videoId="video.title"
        :key="video.title"
        @video-ready-to-play="syncPlayOnAllLoad"
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
  data() {
    return {
      videos: [
        {
          title: "test 1",
          source: "http://52.54.73.208/temp.mp4"
        },
        {
          title: "test 2",
          source: "http://52.54.73.208/temp.mp4"
        },
        {
          title: "test 3",
          source: "http://52.54.73.208/temp.mp4"
        }
      ],
      videoLoadedCount: 0
    };
  },
  methods: {
    // This function starts 'synchronous' play of videos once all are loaded
    syncPlayOnAllLoad: function() {
      this.videoLoadedCount++;
      if (this.videoLoadedCount === this.videos.length) {
        this.$refs.videoPanel.map(e => e.$refs.video.play());
      }
    }
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
  justify-content: space-between;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
