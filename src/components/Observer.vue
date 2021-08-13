<template>
  <div class="observer">

  </div>
</template>

<script>
export default {
    name:"Observer",
    components:{

    },
    data(){
        return {
             observer: null,
        }
    },
     mounted() {
    this.observer = new IntersectionObserver(([entry]) => {
      if (entry && entry.isIntersecting) {
        // console.log("intersecting");
        this.$emit('callNewPage')
        // this.observer.unobserve(this.$el)
      }
    });
    this.observer.observe(this.$el);
  },
  unmounted() {
    this.observer.disconnect();
  },
}
</script>

<style>
.observer{
    height: 1px;
}
</style>