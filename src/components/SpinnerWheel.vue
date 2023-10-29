<template>
  <div class="body">
    <div
      id="spin"
      :class="{ shipanimation: isSpinning }"
      @click="turnWheel()"
    ></div>
    <div
      class="container"
      :style="{ transform: `rotate(${rotationAngle}deg)` }"
    >
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
    return {
      rotationAngle: 0,
      isSpinning: false,
    };
  },
  methods: {
    turnWheel() {
      const number = Math.ceil(Math.random() * 1000);
      this.rotationAngle += number;
      this.isSpinning = true;
      setTimeout(() => {
        this.isSpinning = false;
      }, 1000);
    },
  },
};
</script>

<style scoped>
@import "../assets/styles/SpinnerWheel.css";
</style>
