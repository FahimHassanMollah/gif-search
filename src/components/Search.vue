<template>
    <div class="container mt-4">
        <div class="mb-3">
            <input type="text" class="form-control" v-model="searchKey" @input="search()"  placeholder="Type something to search for awesome gifs">
           
        </div>
    </div>
</template>

<script>
import axios from 'axios';
// api key => wrWFBmgx8706pFTyb7EJGLCCOrNg7jAM
// https://api.giphy.com/v1/gifs/search?api_key=wrWFBmgx8706pFTyb7EJGLCCOrNg7jAM&q=searchKey
export default {
    name:"Search",
    data(){
        return {
            searchKey:'',
            timeOut:null
        }
    },
    methods:{
       async getGifs(){
           const response = await axios.get(`https://api.unsplash.com/search/photos?query=${this.searchKey}&client_id=-T3MrsbumjZ4Xj7wPVLuBpSQ-BbMSF8cthsqTYy4LI4&per_page=30`)
            console.log(response.data)
            this.$emit('fetch-gifs',response.data.results)

        },
         search(){
             clearTimeout(this.timeOut);
             this.timeOut = setTimeout(() => {
                //   this.$emit('fetch-gifs',[])
                 this.getGifs()
             }, 500);
        }
    },
   
}
</script>

<style>

</style>