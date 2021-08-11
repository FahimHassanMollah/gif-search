<template>
  <div class="col-md-3 my-2">
    <div>
      <img :src="gif.images.fixed_height.url" class="img-fluid" alt="">
    </div>
  </div>
</template>

<script>
export default {
  name: "Gif",
  props: ["gif"],
};
</script>

<style>
</style>