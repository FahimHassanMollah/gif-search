<template>
  <div>
    <search></search>
    <gif-list :gifs='gifs'></gif-list>
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
  }
}
</script>

<style>

</style>
