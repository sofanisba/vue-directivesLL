<template>
  <div id="library-wrapper">
    <div class="multiple parallax" v-parallax>
      <img
        v-for="num in [1, 2, 3]"
        :src="imgPath(num)"
        :key="num"
        class="parallax-img"
      />
    </div>

    <div class="single parallax">
      <img id="img-4" v-parallax class="parallax-img" :src="imgPath(4)" />
      <img
        id="img-5"
        v-parallax.overflow
        class="parallax-img"
        :src="imgPath(5)"
      />
      <img
        id="img-6"
        v-parallax="{ orientation: 'right', delay: 1.0, scale: 2.0 }"
        class="parallax-img"
        :src="imgPath(6)"
      />
    </div>
  </div>
</template>

<script>
// https://simpleparallax.com/#examples
import simpleParallax from "simple-parallax-js";

export default {
  name: "library-wrapper",
  directives: {
    parallax: {
      inserted(el, binding) {
        const elementsToBind = el.hasChildNodes() ? el.children : el;
        const defaultOptions = {
          scale: 1.7,
          overflow: false,
          orientation: "left",
        };
        const options = { ...binding.modifiers, ...binding.value };
        el.__parallax__ = new simpleParallax(elementsToBind, {
          ...defaultOptions,
          ...options,
        });
        console.log(el);
      },

      unbind(el) {
        el.__parallax__.destroy();
      },
    },
  },

  methods: {
    imgPath(num) {
      return require(`../assets/parallax_imgs/adventure_time${num}.jpeg`);
    },
  },
};
</script>

<style scoped>
.parallax-img {
  width: 600px;
  margin-top: 100px;
  padding-bottom: 100px;
}
</style>
