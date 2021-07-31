<template>
  <div id="basic-binding">
    <h3>What goes into a binding</h3>
    <pre v-showGuts></pre>
    <!-- <pre v-showGuts:test></pre> -->
    <!-- <pre v-showGuts:test.something></pre> -->
    <!-- <pre v-showGuts:test.something="'thebest'"></pre> -->
  </div>
</template>
<script>
export default {
  name: "BasicBinding",
  directives: {
    showGuts: {
      bind(el, binding, vnode) {
        el.innerText = JSON.stringify(binding, undefined, 2);
      },
    },
  },
};
</script>
