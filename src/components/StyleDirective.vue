<template>
  <div id="style-stuff">
    <h3>Some examples</h3>
    <p>current colour: {{ colours[currentColour] }}</p>
    <button @click="changeColour">Change colour</button>
    <div v-wiggle="colours[currentColour]" class="colour-changer">Look at me!</div>
  </div>
</template>
<script>
import { setTimeout } from "timers";
export default {
  name: "style-stuff",
  data() {
    return {
      colours: [
        "black",
        "blue",
        "cyan",
        "goldenrod",
        "pink",
        "darkmagenta",
        "darkgreen"
      ],
      currentColour: 0
    };
  },
  methods: {
    changeColour() {
      if (this.currentColour === this.colours.length - 1) {
        this.currentColour = 0;
      }
      this.currentColour++;
    }
  },
  directives: {
    wiggle: {
      bind(el, binding) {
        el.style.backgroundColor = binding.value;
      },

      componentUpdated(el, binding) {
        el.style.backgroundColor = binding.value;
        el.classList.add("wiggler");
        setTimeout(() => {
          el.classList.remove("wiggler");
        }, 1000);
      }
    }
  }
};
</script>
<style scoped>
@keyframes shake {
  0% {
    transform: translate(1px, 1px) rotate(0deg);
  }
  10% {
    transform: translate(-1px, -2px) rotate(-1deg);
  }
  20% {
    transform: translate(-3px, 0px) rotate(1deg);
  }
  30% {
    transform: translate(3px, 2px) rotate(0deg);
  }
  40% {
    transform: translate(1px, -1px) rotate(1deg);
  }
  50% {
    transform: translate(-1px, 2px) rotate(-1deg);
  }
  60% {
    transform: translate(-3px, 1px) rotate(0deg);
  }
  70% {
    transform: translate(3px, 1px) rotate(-1deg);
  }
  80% {
    transform: translate(-1px, -1px) rotate(1deg);
  }
  90% {
    transform: translate(1px, 2px) rotate(0deg);
  }
  100% {
    transform: translate(1px, -2px) rotate(-1deg);
  }
}

.wiggler {
  animation: shake 0.3s infinite;
}

.colour-changer {
  padding: 20px;
  font-weight: bold;
  font-size: 20px;
  color: white;
  border-radius: 5px;
  box-shadow: 0px 5px 5px 0 darkcyan;
  width: 150px;
  height: 150px;
  text-align: center;
  vertical-align: middle;
  line-height: 150px;
}

#style-stuff {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
