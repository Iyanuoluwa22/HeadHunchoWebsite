<template>
  <div class="row song-row">

    <div class="col img-max-height">
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
   

    <div class="col">
      <table class="track-info-table">
        <tr>
          <td class="track-info">Track Name</td>
          <td>{{ trackName }}</td>
        </tr>
        <tr>
          <td class="track-info">Artist</td>
          <td>{{ mainArtistName }}</td>
        </tr>
        <tr>
          <td class="track-info">Featuring</td>
          <td>{{ featureArtistName.join(', ') }}</td>
        </tr>
        <tr>
          <td class="track-info">Song Length</td>
          <td>{{ audioDuration }}</td>
        </tr>
        <tr>
          <td class="track-info">Release Date</td>
          <td>-</td>
        </tr>
      </table>
    </div>

    <div class="col song-link-container">
        <div class="row">
          <a href=""><img src="../assets/Images/streaming services/apple-music.png" alt="Apple Music"></a>
        </div>

        <div class="row">
          <a href=""><img src="../assets/Images/streaming services/spotify.png" alt="Spotify"></a>
        </div>

        <div class="row">
          <a href=""><img src="../assets/Images/streaming services/youtube.png" alt="Yotube"></a>
        </div>
        
        <div class="row">
          <a href=""><img src="../assets/Images/streaming services/soundcloud.png" alt="Soundcloud"></a>
        </div>

    </div>
  
    <div class="col add-song">
      <div class="row">
          <p>${{ price }}</p>
      </div>
      <div class="row">
        <button @mouseover="darkenImage" 
              @mouseout="resetImage" >
              Add to Cart
        </button>
      </div>
      
    </div>


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
    },
    price: {
      type : Number,
      default: 0
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
.img-max-height {
  max-height: 250px;
  width: 100%; /* Ensures the container takes full width */
  overflow: hidden; /* Ensures no overflow occurs */
  position: relative; /* Allows for positioning of the image within the container */
}

.ImageSize {
  max-height: 100%; /* Ensures the image respects the container's max height */
  width: auto; /* Maintains aspect ratio */
  object-fit: contain; /* Ensures the image is fully visible without cropping */
  transition: filter 0.3s ease;
  display: block; /* Ensures the image behaves as a block element */
  margin: 0 auto; /* Centers the image horizontally */
}

.track-info-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
  background-image: url('../assets/Images/Galaxy.gif');
  border-radius: 20px;
}

.track-info-table td {
  border: 1px solid #ccc;
  padding: 8px;
  text-align: center;
  font-size-adjust: initial;
}

.add-song {
  display: flex;             /* Enables flexbox layout */
  justify-content: center;   /* Centers content horizontally */
  align-items: center;       /* Centers content vertically */
  flex-direction: column;
}

.add-song button {
  background-color: gold;
  border-radius: 10px;
  color: black;
}

.song-row{
  margin: 20px;
}

.track-info {
  text-decoration: underline;
}

.song-link-container {
    background-color: cornsilk;
    border: 2px solid goldenrod;
    border-radius: 10px;
    max-height: 250px;
    padding: 10px;
    display: flex;
    flex-direction: column;
}

.song-link-container .row {
    height: 25%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.song-link-container img {
    max-height: 50px;
    width: auto;
    object-fit: contain;
    border-radius: 5px;
}


</style>
