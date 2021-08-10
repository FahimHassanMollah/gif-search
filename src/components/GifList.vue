<template>
  <div>
      <gif v-for="gif in gifs" :key="gif" :gif="gif"></gif>
  </div>
</template>

<script>
import Gif from './Gif.vue'
export default {
  components: { Gif },
    name:"GifList",
    props:['gifs']

}
</script>

<style>

</style>