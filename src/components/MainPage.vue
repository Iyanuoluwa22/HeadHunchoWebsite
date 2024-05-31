<template>
  <div class="Main">

    <HeaderPage/>

    <h3 class="PriceNotice">$2 for each song!!!</h3>
    <SongViewer :imgPath="require('@/assets/Shooting Stars/Shooting Stars Cover.png')" 
    :audioPath="require('@/assets/Shooting Stars/Shooting Stars OfficialSongEverth.Del..wav')"/>

    <SongViewer :imgPath="require('@/assets/Letter to the past/cover photo.jpg')" 
    :audioPath="require('@/assets/Letter to the past/Letter to the past w_hu.mp3')"/>

    <SongViewer :imgPath="require('@/assets/Money Reels/Money Reels Official Cover.png')" 
    :audioPath="require('@/assets/Money Reels/Money Reel4 redone3.mp3')"/>     
    
    <FooterPage/>    

  </div>
</template>

<script>
import SongViewer from './SongViewer.vue';
import HeaderPage from './HeaderPage.vue';
import FooterPage from './FooterPage.vue';

export default {
  name: 'MainPage',
  components: {
    SongViewer,
    HeaderPage,
    FooterPage
  }
}
</script>

<style scoped>

.PriceNotice {
  
}

.Main {
  background-color: black;
  text-align: center;
  color: white;
}


</style>
