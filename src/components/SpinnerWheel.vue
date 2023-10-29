<template>
  <div class="body">
    <div id="spin" @click="turnWheel()"></div>
    <div class="container">
      <div class="one">1</div>
      <div class="two">2</div>
      <div class="three">3</div>
      <div class="four">4</div>
      <div class="five">5</div>
      <div class="six">6</div>
      <div class="seven">7</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SpinnerWheel",
  data() {
    return {};
  },
  methods: {
    turnWheel() {
      let container = document.querySelector(".container");
      let spin = document.querySelector("#spin");
      let number = Math.ceil(Math.random() * 1000);
      container.style.transform = "rotate(" + number + "deg)";
      spin.classList.add("anm");
      setTimeout(function () {
        spin.classList.remove("anm");
      }, 1000);
    },
  },
};
</script>

<style scoped>
@import "../assets/styles/SpinnerWheel.css";
</style>
