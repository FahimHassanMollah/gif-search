<template>
  <div class="col-md-3 my-2" >
    <div>
      <img class="img" v-if="gif.urls.full" :src="imgSrc" loading="lazy" alt="">
      <!-- <img v-if="gif.urls.full" :data-src="gif.urls.full" class="img-fluid" loading="lazy" alt=""> -->
      
      <!-- <p v-else>loading........</p> -->
    </div>
  </div>
</template>

<script>

export default {
  name: "Gif",
  props: ["gif"],
  data(){
    return {
      imgSrc:this.gif.urls.full,
      time:null,
     
    }
  },
  created(){
    this.imgSrc =this.imgSrc+"&w=10"
  },
  mounted(){
      clearTimeout(this.time);
      this.time = setTimeout(() => {
         this.imgSrc =this.imgSrc+"&w=1000"
      }, 800);
  },
  methods:{
   

  }
};

</script >

<style >
  .img{
    display: block;
    width: 100%;
    height: 300px;
    object-fit: cover;
  }
</style>