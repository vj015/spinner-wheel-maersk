<template>
  <div class="modal-backdrop">
    <div class="modal">
      <div class="modal-header">
        <div class="header">{{ "Welcome to Maersk Spinning Game!!!" }}</div>
      </div>

      <div class="modal-body">
        <div class="bodyy">
          {{
            "Maersk's core values include Constant Care for their employees and customers, Humbleness in their approach, Uprightness in their business practices, and Our Employees as the foundation of their success. These values reflect their commitment to responsible business, ethics, and prioritizing the well-being of their employees and customers."
          }}
        </div>
        <div class="bodyy1">
          {{
            "The Spinning board includes Maersk Values. Choose your favorite value below; it will determine your ship's fate. Additionally, the wheel includes Maersk's core characteristics: Diversity, Equity, and Inclusion (DEI) and Carbon Neutrality, which can be bonus gifts if they align with your spin."
          }}
        </div>
      </div>
      <div class="main-container">
        <h2>Which Maersk Value, you liked most ?</h2>
        <div class="radio-buttons">
          <label class="custom-radio">
            <input
              type="radio"
              name="radio"
              value="1"
              v-model="selectedValue"
            />
            <span class="radio-btn"
              ><i class="las la-check"></i>
              <div class="hobbies-icon">
                <img
                  src="https://img.freepik.com/free-vector/teamwork-concept-landing-page_52683-20165.jpg?size=626&ext=jpg"
                />
                <h3 class="">Our Employees</h3>
              </div>
            </span>
          </label>
          <label class="custom-radio">
            <input
              type="radio"
              name="radio"
              value="2"
              v-model="selectedValue"
            />
            <span class="radio-btn"
              ><i class="las la-check"></i>
              <div class="hobbies-icon">
                <img
                  src="https://img.freepik.com/free-vector/hand-drawn-employee-benefits-illustration_23-2149531332.jpg?size=626&ext=jpg"
                />
                <h3 class="">Constant Care</h3>
              </div>
            </span>
          </label>
          <label class="custom-radio">
            <input
              type="radio"
              name="radio"
              value="3"
              v-model="selectedValue"
            />
            <span class="radio-btn"
              ><i class="las la-check"></i>
              <div class="hobbies-icon">
                <img
                  src="https://img.freepik.com/free-vector/business-ethics-concept-illustration_114360-8860.jpg?size=626&ext=jpg"
                />
                <h3 class="">Uprightness</h3>
              </div>
            </span>
          </label>
          <label class="custom-radio">
            <input
              type="radio"
              name="radio"
              value="4"
              v-model="selectedValue"
            />
            <span class="radio-btn"
              ><i class="las la-check"></i>
              <div class="hobbies-icon">
                <img
                  src="https://img.freepik.com/free-vector/flat-design-csr-concept-illustrated_23-2148927501.jpg?size=626&ext=jpg"
                />
                <h3 class="">Humbleness</h3>
              </div>
            </span>
          </label>
          <label class="custom-radio">
            <input
              type="radio"
              name="radio"
              value="5"
              v-model="selectedValue"
            />
            <span class="radio-btn"
              ><i class="las la-check"></i>
              <div class="hobbies-icon">
                <img
                  src="https://img.freepik.com/free-photo/standard-quality-control-collage_23-2149631013.jpg?size=626&ext=jpg"
                />
                <h3 class="">Our Name</h3>
              </div>
            </span>
          </label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalComponent",
  data() {
    return {
      selectedValue: null,
    };
  },
  methods: {
    close() {
      this.$emit("close");
    },
  },
  watch: {
    selectedValue(newValue) {
      if (newValue) {
        this.$emit("SelectedValue", newValue);
        setTimeout(() => {
          this.$emit("close");
        }, 1000);
      }
    },
  },
};
</script>

<style>
.bodyy .bodyy1 {
  font-family: serif;
  color: #00243d;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  background: #ffffff;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  flex-direction: column;
  height: 600px;
  width: 600px;
}

.modal-header {
  padding: 15px;
  display: flex;
}

.modal-header {
  position: relative;
  border-bottom: 1px solid #eeeeee;
  color: #00243d;
  justify-content: space-between;
  height: 75px;
  font-size: xx-large;
  font-family: fantasy;
}
.modal-header div {
  top: 10px;
}

.modal-body {
  position: relative;
  padding: 20px 10px;
}
.main-container {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.main-container h2 {
  margin: 110px 0 10px 0;
  color: #00243d;
  font-family: math;
}

.radio-buttons {
  width: 100%;
  margin: 0 auto;
  text-align: center;
}

.custom-radio input {
  display: none;
}

.radio-btn {
  margin: 10px;
  width: 220px;
  height: 240px;
  border: 3px solid transparent;
  display: inline-block;
  border-radius: 10px;
  position: relative;
  text-align: center;
  box-shadow: 0 0 20px #c3c3c367;
  cursor: pointer;
}

.radio-btn > i {
  color: #ffffff;
  background-color: #00243d;
  font-size: 20px;
  position: absolute;
  top: -15px;
  left: 50%;
  transform: translateX(-50%) scale(2);
  border-radius: 50px;
  padding: 3px;
  transition: 0.5s;
  pointer-events: none;
  opacity: 0;
}

.radio-btn .hobbies-icon {
  width: 150px;
  height: 150px;
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.radio-btn .hobbies-icon img {
  display: block;
  width: 100%;
  margin-bottom: 20px;
  height: 150px;
}
.radio-btn .hobbies-icon i {
  color: #00243d;
  line-height: 80px;
  font-size: 60px;
}

.radio-btn .hobbies-icon h3 {
  color: #00243d;
  font-size: 18px;
  font-weight: 300;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.custom-radio input:checked + .radio-btn {
  border: 2px solid #00243d;
}

.custom-radio input:checked + .radio-btn > i {
  opacity: 1;
  transform: translateX(-50%) scale(1);
}
</style>
