<template>
  <div id="hooks">
    <button @click="num++">Click me!</button>
    <h3>Directive Hooks</h3>
    <pre class="hooks" v-showHooks="num">
      Click counter: {{num}}
    </pre>
  </div>
</template>
<script>
export default {
  name: "hooks",
  data() {
    return {
      num: 1
    };
  },
  directives: {
    showHooks: {
      bind(el, binding, vnode) {
        alert("bind");
        el.appendChild(document.createTextNode("bind"));
        el.appendChild(document.createElement("br"));
      },

      inserted(el, binding, vnode) {
        alert("inserted");
        el.appendChild(document.createTextNode("inserted"));
        el.appendChild(document.createElement("br"));
      },

      update(el, binding, vnode, oldVnode) {
        alert("update");
        el.appendChild(
          document.createTextNode(
            `update: oldValue: ${binding.oldValue}, value: ${binding.value}`
          )
        );
        el.appendChild(document.createElement("br"));
      },

      componentUpdated(el, binding, vnode, oldVnode) {
        alert("componentUpdated");
        el.appendChild(
          document.createTextNode(
            `componentUpdated: oldValue: ${binding.oldValue}, value: ${binding.value}`
          )
        );
        el.appendChild(document.createElement("br"));
      },
      unbind() {
        alert("unbind");
      }
    }
  }
};
</script>
<style>
.hooks {
  background-color: darkmagenta;
}
</style>
