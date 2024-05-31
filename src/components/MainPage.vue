<template>
  <div class="Main">
    <div class="Title"><h1 id="satisfy-regular">HUNCHO</h1></div>
    
    <ul>
      <li><a href="">Merch</a></li>
      <li><a href="">About Me</a></li>
    </ul>
    
    <SongViewer :imgPath="require('@/assets/Shooting Stars/Shooting Stars Cover.png')" class="SongImage"/>
          
    <div><p> <a href="">Subscribe</a> to Huncho's newsletter</p></div>
    
  </div>
</template>

<script>
import SongViewer from './SongViewer.vue';

export default {
  name: 'MainPage',
  components: {
    SongViewer
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Satisfy&display=swap');

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

.Title {
  background-color: brown;
  padding: 1px;
}

.Main {
  background-color: black;
  text-align: center;
  color: white;
}

#satisfy-regular {
  font-family: "Satisfy", cursive;
  font-weight: 400;
  font-style: normal;
}
</style>
