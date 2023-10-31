<template>
  <div>
    <div class="body" :class="isModalVisible || showResult ? 'fade-main' : ''">
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
    <div class="formatModal">
      <ModalComponent
        v-show="isModalVisible"
        @close="closeModal"
        @SelectedValue="SelectedValue"
      />
      <ResultModal
        v-show="showResult"
        :first="first"
        :constellation="constellation"
        :fail="fail"
      />
    </div>
  </div>
</template>

<script>
import ModalComponent from "./ModalComponent.vue";
import ResultModal from "./ResultModal.vue";
export default {
  name: "SpinnerWheel",
  components: {
    ModalComponent,
    ResultModal,
  },
  data() {
    return {
      rotationAngle: 0,
      isSpinning: false,
      count: 0,
      winner: 0,
      nowinner: false,
      isModalVisible: false,
      selectedVal: "",
      showResult: false,
      first: false,
      constellation: false,
      fail: false,
    };
  },
  mounted() {
    this.showModal();
  },
  methods: {
    showModal() {
      this.isModalVisible = true;
    },
    showResultModal() {
      this.showResult = true;
    },
    // closeResultModal() {
    //   this.showResult = false;
    // },
    closeModal() {
      this.isModalVisible = false;
    },
    SelectedValue(val) {
      this.selectedVal = val;
    },
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
        this.fail = true;
        this.first = false;
        this.constellation = false;
      } else {
        if (this.winner === this.selectedVal) {
          this.fail = false;
          this.first = true;
          this.constellation = false;
          this.nowinner = false;
        } else if (this.winner === 6 || this.winner === 7) {
          this.fail = false;
          this.first = false;
          this.constellation = true;
          this.nowinner = false;
        } else {
          this.fail = true;
          this.first = false;
          this.constellation = false;
          this.nowinner = true;
        }
        console.log("Result Overlapping one", this.winner);
      }
      this.showResultModal();
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
