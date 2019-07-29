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
      }
    }
  }
};
</script>

<style lang="css" scoped>
#basic-binding {
}
pre {
  font-size: 20px;
  padding: 20px;
  background-color: darkmagenta;
  border-radius: 10px;
  box-shadow: 0px 5px 5px 0 darkcyan;
}
</style>

