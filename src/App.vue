<template>
  <div>
    <search @fetch-gifs="fetchGifs"></search>
    <gif-list :gifs="gifs"></gif-list>
  </div>
</template>

<script>

import GifList from './components/GifList.vue'
import Search from './components/Search.vue'


export default {
  name: 'App',
  components: {
    Search,
    GifList,
  
   
  },
  data(){
    return {
      gifs:[]
    }
  },
  methods:{
    fetchGifs(result){
      this.gifs = result
    }
  }
}
</script>

<style>

</style>
