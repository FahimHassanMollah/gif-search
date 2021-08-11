<template>
  <div class="container">
    <div class="row">
       <gif v-for="gif in gifs" :key="gif" :gif="gif"></gif>
    </div>
    
  </div>
</template>

<script>

import Gif from './Gif.vue'
export default {
  components: { Gif },
    name:"GifList",
    props:['gifs'],
    created(){
      console.log(this.gifs)
    }

}

</script>

<style>

</style>