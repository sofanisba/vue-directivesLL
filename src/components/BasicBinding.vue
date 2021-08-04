<template>
  <div id="basic-binding">
    <h3>What goes into a binding</h3>
    <button @click="showMeMore">Show More</button>

    <pre
      :class="{ hidden: elShown < 3 }"
      v-showGuts:test.something="'thebest'"
    />
    <pre :class="{ hidden: elShown < 2 }" v-showGuts:test.something />
    <pre :class="{ hidden: elShown < 1 }" v-showGuts:test />
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
