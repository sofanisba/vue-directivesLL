<template>
  <div id="app">
    <h1>{{steps[this.stepIndex]}}</h1>
    <BasicBinding />
  </div>
</template>

<script>
import BasicBinding from "./components/BasicBinding.vue";

export default {
  name: "app",
  components: {
    BasicBinding
  },
  data() {
    return {
      stepIndex: 0,
      steps: ["BasicBinding"]
    };
  },
  computed: {
    currentStep() {
      return this.steps[this.stepIndex];
    }
  }
};
</script>

<style>
body {
  background-color: lightseagreen;
  font-family: "Courier New", Courier, monospace;
  color: lightcyan;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
