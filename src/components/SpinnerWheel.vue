<template>
  <div class="body">
    <button id="spin" @click="turnWheel()">Spin</button>
    <span class="arrow"></span>
    <div class="container">
      <div class="one">1</div>
      <div class="two">2</div>
      <div class="three">3</div>
      <div class="four">4</div>
      <div class="five">5</div>
      <div class="six">6</div>
      <div class="seven">7</div>
      <div class="eight">8</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SpinnerWheel",
  methods: {
    turnWheel() {
      let container = document.querySelector(".container");
      let number = Math.ceil(Math.random() * 1000);
      container.style.transition = "transform 0.5s";
      container.style.transform = "rotate(" + number + "deg)";
      number += Math.ceil(Math.random() * 1000);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import '../assets/styles/SpinnerWheel.css';
</style>
