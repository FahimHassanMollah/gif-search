<template>
  <div class="container">
    <div class="row">
       <gif v-for="gif in gifs" :key="gif" :gif="gif"></gif>
    </div>
    
  </div>
</template>

<script>

import Gif from './Gif.vue'
// const options = {
//   root: null,
//   threshold: 0
// };
export default {
  components: { Gif },
    name:"GifList",
    props:['gifs'],
    data(){
      return {
        
      }
    },
    created(){
      console.log(this.gifs)
    },
    // mounted(){
    //    this.observer = new IntersectionObserver(this.callback, options);
    // this.observer.observe(this.$refs.divAsTarget);
    // }

}

</script>

<style>

</style>