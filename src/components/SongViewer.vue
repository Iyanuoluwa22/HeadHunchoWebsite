<template>
    <div>
      <img :src="imgPath" alt="Image Here" class="ImageSize">
    </div>
  </template>
  
  <script>
  export default {
    name: 'SongViewer',
    props: {
      imgPath: {
        type: String,
        required: true
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