<template>
  <div class="body">
    <div class="arrow" id="crane">
      <img src="../assets/crane-icon.png" alt="Icon" />
    </div>
    <div
      id="spin"
      :class="{ shipanimation: isSpinning }"
      @click="turnWheel()"
    ></div>
    <div
      class="container"
      :style="{ transform: `rotate(${rotationAngle}deg)` }"
    >
      <div class="one" id="segment-1">
        <span>{{ "Our Employees" }}</span>
      </div>
      <div class="two" id="segment-2">
        <span>{{ "Constant Care" }}</span>
      </div>
      <div class="three" id="segment-3">
        <span>{{ "Uprightness" }}</span>
      </div>
      <div class="four" id="segment-4">
        <span>{{ "Humbleness" }}</span>
      </div>
      <div class="five" id="segment-5">
        <span>{{ "Our Name" }}</span>
      </div>
      <div class="six" id="segment-6">
        <span>{{ "DEI" }}</span>
      </div>
      <div class="seven" id="segment-7">
        <span>{{ "Carbon Neutral" }}</span>
      </div>
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
      count: 0,
      winner: 0,
      nowinner: false,
      message: "Our \n Employees",
    };
  },
  methods: {
    elementsOverlap(el1, el2) {
      console.log("function called");
      const domRect1 = el1.getBoundingClientRect();
      const domRect2 = el2.getBoundingClientRect();

      return !(
        domRect1.top > domRect2.bottom ||
        domRect1.right < domRect2.left ||
        domRect1.bottom < domRect2.top ||
        domRect1.left > domRect2.right
      );
    },
    getSegmentElement(index) {
      return document.getElementById(`segment-${index}`);
    },
    getCraneElement() {
      return document.getElementById("crane");
    },
    checkForWinner() {
      for (let i = 1; i < 8; i++) {
        const segment = this.getSegmentElement(i);
        const crane = this.getCraneElement();

        if (this.elementsOverlap(segment, crane)) {
          this.count++;
          this.winner = i;
        }
      }

      if (this.count > 1) {
        this.nowinner = true;
        this.winner = null;
      } else {
        this.nowinner = false;
        console.log("Result Overlapping one", this.winner);
      }
    },
    turnWheel() {
      const number = Math.ceil(Math.random() * 1000);
      this.rotationAngle += number;
      this.isSpinning = true;
      setTimeout(() => {
        this.isSpinning = false;
        this.checkForWinner();
      }, 2000);
    },
  },
};
</script>

<style scoped>
@import "../assets/styles/SpinnerWheel.css";
</style>
