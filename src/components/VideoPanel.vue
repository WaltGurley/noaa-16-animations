<template>
  <div class="video-panel">
    <h3>Source {{ videoId }}</h3>
    <video class="video" autoplay muted="true" controls>
      <source :src="videoSrc" type="video/mp4">
    </video>
  </div>
</template>

<script>
export default {
  name: "VideoPanel",
  props: {
    videoSrc: String,
    videoId: Number
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@media screen and (max-width: 425px) {
  .video-panel {
    width: 98%;
  }
}

@media screen and (min-width: 426px) {
  .video-panel {
    width: 50%;
  }
}

@media screen and (min-width: 769px) {
  .video-panel {
    width: 33%;
  }
}

.video {
  width: 100%;
}
</style>
