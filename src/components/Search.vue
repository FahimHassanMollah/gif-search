<template>
    <div class="container mt-4">
        <div class="mb-3">
            <input type="text" class="form-control" v-model="searchKey" @input="getGifs()"  placeholder="Type something to search for awesome gifs">
           
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
            searchKey:''
        }
    },
    methods:{
       async getGifs(){
           const response = await axios.get(`https://api.giphy.com/v1/gifs/search?api_key=wrWFBmgx8706pFTyb7EJGLCCOrNg7jAM&q=${this.searchKey}`)
            console.log(response.data)
        }
    }
}
</script>

<style>

</style>