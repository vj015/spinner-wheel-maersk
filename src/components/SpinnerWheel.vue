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
    elementsOverlap() {
      console.log("function called");
      const el1 = document.getElementById("arr");
      const el2 = document.getElementById("arr1");
      const domRect1 = el1.getBoundingClientRect();
      const domRect2 = el2.getBoundingClientRect();

      return !(
        domRect1.top > domRect2.bottom ||
        domRect1.right < domRect2.left ||
        domRect1.bottom < domRect2.top ||
        domRect1.left > domRect2.right
      );
    },
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
