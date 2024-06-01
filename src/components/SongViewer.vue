<template>
  <div>
    <img 
      :src="imgPath" 
      alt="Image Here" 
      class="ImageSize" 
      @mouseover="darkenImage" 
      @mouseout="resetImage" 
      @click="toggleClick"
    >
    <audio ref="audio" :src="audioPath" @loadedmetadata="getAudioDuration"></audio>
  </div>

  <table class="track-info-table">
    <tr>
      <td>Track Name</td>
      <td>{{ trackName }}</td>
    </tr>
    <tr>
      <td>Artist</td>
      <td>{{ mainArtistName }}</td>
    </tr>
    <tr>
      <td>Featuring</td>
      <td>{{ featureArtistName.join(', ') }}</td>
    </tr>
    <tr>
      <td>Song Length</td>
      <td>{{ audioDuration }}</td>
    </tr>
  </table>

  <button>Add to Cart</button>
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
    },
    trackName: {
      type: String,
      default: '-'
    },
    mainArtistName: {
      type: String,
      default: '-'
    },
    featureArtistName: {
      type: Array,
      default: () => ['-']
    }
  },
  data() {
    return {
      clicked: false,
      audioDuration: null
    };
  },
  methods: {
    toggleClick() {
      this.clicked = !this.clicked;
      const audio = this.$refs.audio;
      if (this.clicked) {
        this.playAudio(audio);
      } else {
        this.pauseAudio(audio);
      }
    },
    playAudio(audio) {
      const startTime = 0; // start time in seconds
      const duration = 30; // duration to play in seconds

      audio.currentTime = startTime;
      audio.play();

      this.playTimeout = setTimeout(() => {
        audio.pause();
        this.clicked = false; // Reset clicked state after playback
      }, duration * 1000);
    },
    pauseAudio(audio) {
      audio.pause();
      clearTimeout(this.playTimeout); // Clear any ongoing timeout to prevent auto-pause
    },
    darkenImage(event) {
      event.target.style.filter = 'brightness(70%)';
    },
    resetImage(event) {
      event.target.style.filter = 'brightness(100%)';
    },
    getAudioDuration() {
      const audio = this.$refs.audio;
      this.audioDuration = this.formatDuration(audio.duration);
    },
    formatDuration(seconds) {
      const minutes = Math.floor(seconds / 60);
      const remainingSeconds = Math.floor(seconds % 60);
      return `${minutes}:${remainingSeconds < 10 ? '0' : ''}${remainingSeconds}`;
    }
  },
  beforeUnmount() {
    clearTimeout(this.playTimeout); // Clean up timeout when component is destroyed
  }
}
</script>

<style scoped>
.ImageSize {
  max-height: 200px;
  width: auto;
  transition: filter 0.3s ease;
}

.track-info-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

.track-info-table td {
  border: 1px solid #ccc;
  padding: 8px;
  text-align: left;
}

.track-info-table tr:nth-child(even) {
  background-color: #f9f9f9;
}
</style>
