<template>
  <div class="modal-backdrop1">
    <div class="modal1">
      <div class="card" v-if="first || constellation">
        <button type="button" class="btn-close11" @click="close">x</button>
        <img src="../assets/successboy.jpg" alt="Success" />
        <div class="card-text">
          <h2>Congratulations!!</h2>
          <p v-if="first">You get the first prize</p>
          <p v-if="constellation">You get prize!</p>
        </div>
      </div>
      <div class="card" v-if="fail">
        <button type="button" class="btn-close11" @click="close">x</button>
        <img
          src="https://img.freepik.com/free-psd/x-symbol-isolated_23-2150500369.jpg?size=626&ext=jpg"
          alt="Success"
        />
        <div class="card-text-fail">
          <h2>OOPS!!</h2>
          <p>Better Luck Next Time!</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "ResultModal",
  props: ["first", "constellation", "fail"],
  methods: {
    close() {
      this.$emit("close");
    },
  },
};
</script>
<style>
.modal-backdrop1 {
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

.modal1 {
  background: #ffffff;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  flex-direction: column;
  height: 486px;
  width: 461px;
}

.btn-close11 {
  position: relative;
  top: 0px;
  right: -180px;
  border: none;
  font-size: 40px;
  padding: 10px;
  cursor: pointer;
  font-weight: bold;
  color: #0d0e0f;
  background: transparent;
}
.card {
  width: 461px;
  border-radius: 5px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  text-align: center;
}

.card img {
  width: 425px;
  height: 283px;
}

.card-text {
  padding: 15px;
  background-color: #42b0d5;
}
.card-text-fail {
  padding: 15px;
  background-color: rgb(255 63 18);
}
.card-text h2,
p {
  font-family: fantasy;
}
</style>
