<template>
  <div id="app">
    <header>
      <h1>NOAA-16</h1>
      <h2>Weather Satellite Data</h2>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Laudantium maxime nostrum nesciunt consectetur velit fugiat tenetur voluptatum rem unde magni? Quibusdam delectus modi quisquam nulla nesciunt dolorem. Soluta, quis sunt?
      </p>
    </header>
    <main class="video-container">
      <VideoPanel
        ref="videoPanel"
        v-for="video in videos"
        :videoUrl="video.url"
        :videoId="video.title"
        :videoInfo="video.info"
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
          title: "Low Vapor",
          url: "http://52.54.73.208/walt/low_vapor.mp4",
          info: "This is test source 2. It shows some cool satellite data"
        },
        {
          title: "Mid Vapor",
          url: "http://52.54.73.208/walt/mid_vapor.mp4",
          info: "This is test source 3. It shows some cool satellite data"
        },
        {
          title: "High Vapor",
          url: "http://52.54.73.208/walt/high_vapor.mp4",
          info: "This is test source 3. It shows some cool satellite data"
        },
        {
          title: "Visible IR",
          url: "http://52.54.73.208/walt/vis_IR.mp4",
          info: "This is test source 1. It shows some cool satellite data"
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

@media screen and (min-width: 2880px) {
  body {
    margin: 0;
    background-color: #2c3e50;
  }

  #app {
    color: #f7f7f7;
  }

  h1 {
    font-size: 4em;
  }

  h2 {
    font-size: 3em;
  }

  h3 {
    font-size: 2.34em;
  }

  p {
    font-size: 2em;
  }

  #app {
    margin-top: 0;
  }

  header {
    height: 320px;
    margin: 0 1em;
    display: flex;
    flex-direction: row;
    align-items: baseline;
  }

  .video-container {
    height: calc(100vh-320px);
    justify-content: space-evenly;
  }
}
</style>
