<template>
  <div class="video-panel">
    <h3>Source {{ videoId }}</h3>
    <p>{{  videoInfo }}</p>
    <video
      class="video"
      muted="true"
      controls
      loop
      ref="video"
      @canplaythrough="$emit('video-ready-to-play')"
    >
      <source :src="videoSrc" type="video/mp4" />
    </video>
  </div>
</template>

<script>
export default {
  name: "VideoPanel",
  props: {
    videoSrc: String,
    videoId: String,
    videoInfo: String
  },
  methods: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@media screen and (max-width: 425px) {
  .video-panel {
    width: 100%;
  }
}

@media screen and (min-width: 426px) {
  .video-panel {
    width: 49%;
  }
}

@media screen and (min-width: 769px) {
  .video-panel {
    width: 32%;
  }
}

.video-panel {
  border-radius: 6px;
  box-shadow: 0 0 4px #aaa;
  padding: 1px;
}

.video {
  width: 100%;
}
</style>
