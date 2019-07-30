<template>
  <div id="app">
    <h1>{{steps[this.stepIndex]}}</h1>
    <component :is="currentStep" />
    <div class="buttons">
      <button @click="decrement">Prev</button>
      <button @click="increment">Next</button>
    </div>
  </div>
</template>

<script>
import BasicBinding from "./components/BasicBinding.vue";
import Hooks from "./components/Hooks.vue";
import StyleDirective from "./components/StyleDirective.vue";
import SomethingUseful from "./components/SomethingUseful.vue";

export default {
  name: "app",
  components: {
    BasicBinding,
    Hooks,
    StyleDirective,
    SomethingUseful
  },

  data() {
    return {
      stepIndex: 0,
      steps: ["BasicBinding", "Hooks", "StyleDirective", "SomethingUseful"]
    };
  },

  methods: {
    increment() {
      return this.stepIndex === this.steps.length - 1
        ? false
        : this.stepIndex++;
    },
    decrement() {
      return this.stepIndex === 0 ? false : this.stepIndex--;
    }
  },

  computed: {
    currentStep() {
      return this.steps[this.stepIndex];
    }
  }
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

body {
  background-color: lightseagreen;
  font-family: "Courier New", Courier, monospace;
  color: lightcyan;
}

pre {
  font-size: 20px;
  padding: 20px;
  background-color: darkmagenta;
  border-radius: 10px;
  box-shadow: 0px 5px 5px 0 darkcyan;
}

h3 {
  text-align: center;
}

button {
  background-color: darkorange;
  border: 0;
  padding: 5px 20px;
  margin: 10px;
  border-radius: 5px;
  color: white;
  font-weight: bold;
  text-transform: uppercase;
  box-shadow: 2px 2px 2px darkcyan;
}
</style>
