<template>
  <MainPage/>
</template>

<script>
import MainPage from './components/MainPage.vue'

export default {
  name: 'App',
  components: {  
    MainPage
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Jaini+Purva&family=Satisfy&family=Teko:wght@300..700&display=swap');

#app {
  font-family: 'Teko','Satisfy', 'Bebas Neue', 'Jaini Purva', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
