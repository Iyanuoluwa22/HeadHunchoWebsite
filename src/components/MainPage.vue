<template>
  <div class="Main">

    <HeaderPage/>
    <NavPage/>

    <SongViewer :imgPath="require('@/assets/Shooting Stars/Shooting Stars Cover.png')" 
    :audioPath="require('@/assets/Shooting Stars/Shooting Stars OfficialSongEverth.Del..wav')"
    trackName = "Shooting Stars"
    mainArtistName="HeadHuncho"
    price = 2.00
    />

    <SongViewer :imgPath="require('@/assets/Letter to the past/cover photo.jpg')" 
    :audioPath="require('@/assets/Letter to the past/Letter to the past w_hu.mp3')"
    trackName = "Letter to the Past"
    mainArtistName="Nu x HeadHuncho"
    price = 2.00
    />

    <SongViewer :imgPath="require('@/assets/Money Reels/Money Reels Official Cover.png')" 
    :audioPath="require('@/assets/Money Reels/Money Reel4 redone3.mp3')"
    trackName = "Money Reels"
    mainArtistName="HeadHuncho x ItsMane"
    price = 2.00
    />     
    
    <FooterPage/>    

  </div>
</template>

<script>
import SongViewer from './SongViewer.vue';
import HeaderPage from './HeaderPage.vue';
import FooterPage from './FooterPage.vue';
import NavPage from './NavBar.vue'

export default {
  name: 'MainPage',
  components: {
    SongViewer,
    HeaderPage,
    FooterPage,
    NavPage
  }
}
</script>

<style scoped>

.Main {
  background-color: black;
  text-align: center;
  color: white;
}


</style>
