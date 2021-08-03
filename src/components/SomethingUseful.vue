<template>
  <div id="something-useful">
    <h3>Debounce</h3>
    <p>{{ val }}</p>
    <input type="text" v-debounce v-model.lazy="val" />
  </div>
</template>
<script>
const debounce = (fn, delay) => {
  var timeoutID = null;
  return function () {
    clearTimeout(timeoutID);
    var args = arguments;
    timeoutID = setTimeout(function () {
      fn.apply(this, args);
    }, delay);
  };
};
export default {
  name: "something-useful",
  data() {
    return {
      val: "",
    };
  },
  directives: {
    debounce: (el, binding) => {
      const delay = parseInt(binding.value) || 500;
      el.oninput = debounce(function () {
        el.dispatchEvent(new Event("change"));
      }, delay);
    },
  },
};
</script>
