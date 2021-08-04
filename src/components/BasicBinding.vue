<template>
  <div id="basic-binding">
    <h3>What goes into a binding</h3>
    <button @click="showMeMore">Show More</button>

    <pre v-if="elShown >= 3" v-showGuts:test.something="'thebest'" />
    <pre v-if="elShown >= 2" v-showGuts:test.something />
    <pre v-if="elShown >= 1" v-showGuts:test />
    <pre v-showGuts></pre>
  </div>
</template>
<script>
export default {
  name: "BasicBinding",
  data() {
    return {
      elShown: 0,
    };
  },

  directives: {
    showGuts: {
      bind(el, binding) {
        el.innerText = JSON.stringify(binding, undefined, 2);
      },
    },
  },

  methods: {
    showMeMore() {
      this.elShown++;
    },
  },
};
</script>
<style scoped>
.hidden {
  display: none;
}
</style>
