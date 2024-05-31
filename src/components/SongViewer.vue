<template>
    <div>
      <img :src="imgPath" alt="Image Here" class="ImageSize">
      <audio ref="audio" :src="audioPath" controls @play="playAudioSegment"></audio>
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
      playAudioSegment() {
        const audio = this.$refs.audio;
        const startTime = 0; // start time in seconds
        const duration = 30; // duration to play in seconds
  
        audio.currentTime = startTime;
        setTimeout(() => {
          audio.pause();
        }, duration * 1000);
      }
    }
  }
  </script>
  
  <style scoped>
  .ImageSize {
    max-height: 200px;
    width: auto;
  }
  </style>
  