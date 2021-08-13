<template>
  <div class="col-md-3 my-2">
    <div>
      <img
        class="img"
        v-if="gif.urls.full"
        :src="imgSrc"
        loading="lazy"
        alt=""
      />
      <!-- <img v-if="gif.urls.full" :data-src="gif.urls.full" class="img-fluid" loading="lazy" alt=""> -->

      <!-- <p v-else>loading........</p> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "Gif",
  props: ["gif"],
  data() {
    return {
      imgSrc: this.gif.urls.full,
      time: null,
      observer: null,
    };
  },
  created() {
    this.imgSrc = this.imgSrc + "&w=10";
  },
  mounted() {
    this.observer = new IntersectionObserver(([entry]) => {
      if (entry && entry.isIntersecting) {
        console.log("intersecting");
        clearTimeout(this.time);
        this.time = setTimeout(() => {
          this.imgSrc = this.imgSrc + "&w=1000";
          this.observer.unobserve(this.$el)
        }, 800);
      }
    });
    this.observer.observe(this.$el);
  },
  unmounted() {
    this.observer.disconnect();
  },
  methods: {},
};
</script >

<style >
.img {
  display: block;
  width: 100%;
  height: 300px;
  object-fit: cover;
}
</style>