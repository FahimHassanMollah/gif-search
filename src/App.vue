<template>
  <div>
    <div class="container mt-4">
      <div class="mb-3">
        <input
          type="text"
          class="form-control"
          v-model="searchKey"
          @input="search()"
          placeholder="Type something to search for awesome gifs"
        />
      </div>
    </div>
    <gif-list :gifs="gifs"></gif-list>
    <Observer @callNewPage="callNewPage"></Observer>
  </div>
</template>

<script>
import GifList from "./components/GifList.vue";
import Observer from "./components/Observer.vue";
import axios from 'axios';

export default {
  name: "App",
  components: {
    GifList,
    Observer,
  },
  data() {
    return {
      gifs: [],
      searchKey: "",
      timeOut: null,
      page:1
    };
  },
  methods: {

    async getGifs() {
      const response = await axios.get(
        `https://api.unsplash.com/search/photos?query=${this.searchKey}&client_id=-T3MrsbumjZ4Xj7wPVLuBpSQ-BbMSF8cthsqTYy4LI4&page=${this.page}`
      );
      console.log(response.data);
      let updateArray = response.data.results;
     this.gifs =[...this.gifs,...updateArray]
    },
    search() {
      clearTimeout(this.timeOut);
      this.timeOut = setTimeout(() => {
        //   this.$emit('fetch-gifs',[])
        this.getGifs();
      }, 500);
    },
    callNewPage(){
      ++this.page
      console.log('call new page')
      this.getGifs()
    }
  },
};
</script>

<style>
</style>
