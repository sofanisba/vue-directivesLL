<template>
  <div id="something-really-useful" class="flex">
    <button @click="switchSvg">Swap'em</button>
    <div v-svg="currentSvg" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentSvgIndex: 0,
      sgvList: ["dribbble", "world-map", "dribbble-vector-ball", "confetti"],
    };
  },

  computed: {
    currentSvg() {
      return this.sgvList[this.currentSvgIndex];
    },
  },

  directives: {
    svg(el, binding) {
      const svgSrc = require(`../assets/${binding.value}.svg`);
      const imgEl = document.createElement("img");
      imgEl.src = svgSrc;
      if (el.childNodes.length) {
        el.replaceChild(imgEl, el.childNodes[0]);
      } else {
        el.appendChild(imgEl);
      }
    },
  },

  methods: {
    switchSvg() {
      if (this.currentSvgIndex < this.sgvList.length - 1) {
        return this.currentSvgIndex++;
      }

      this.currentSvgIndex = 0;
    },
  },
};
</script>
<style scoped></style>
