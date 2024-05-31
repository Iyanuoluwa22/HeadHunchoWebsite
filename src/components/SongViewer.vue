<template>
  <div>
    <img :src="imgPath" alt="Image Here" class="ImageSize" @mouseover="darkenImage" @mouseout="resetImage" @click="playAudio">
    <audio ref="audio" :src="audioPath"></audio>
    <button>Add to Cart</button>
  </div>
</template>

<script>
export default {
  name: 'SongViewer',
  props: {
    imgPath: {
      type: String,
      required: true
    },
    audioPath: {
      type: String,
      required: true
    }
  },
  methods: {
    playAudio() {
      const audio = this.$refs.audio;
      const startTime = 0; // start time in seconds
      const duration = 30; // duration to play in seconds

      audio.currentTime = startTime;
      audio.play();

      setTimeout(() => {
        audio.pause();
      }, duration * 1000);
    },
    darkenImage(event) {
      event.target.style.filter = 'brightness(70%)';
    },
    resetImage(event) {
      event.target.style.filter = 'brightness(100%)';
    }
  }
}
</script>

<style scoped>
.ImageSize {
  max-height: 200px;
  width: auto;
  transition: filter 0.3s ease;
}
</style>