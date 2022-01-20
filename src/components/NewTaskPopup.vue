<template>
  <div class="popup-wrap">
    <input type="text" id="newTask" placeholder="New Task" />
    <div class="button" @click="addTask()">Done</div>
    <div class="button" @click="$emit('close')">Cancel</div>
  </div>
</template>

<script>
export default {
  name: "NewTaskPopup",

  data() {
    return {};
  },
  methods: {
    addTask() {
      let newTask = document.getElementById("newTask").value;
      this.$emit("task", newTask);
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
.popup-wrap {
  position: absolute;
  top: 30%;
  left: 25%;
  width: 40%;
  height: 370px;
  z-index: 10;
  background: white;
  border: 2px solid #116f8b;
  border-radius: 30px;
}

input {
  position: relative;
  left: 84px;
  width: 67%;
  top: 51px;
  height: 153px;
  border: 2px solid #d5f5ff;
  border-radius: 40px;
  font-size: 34px;
}

.button {
  padding-left: 15px;
  width: 34%;
  height: 50px;
  z-index: 10;
  display: inline-grid;
  margin: 25px;
  position: relative;
  left: 30px;
  top: 90px;
  font-size: 40px;
  border-radius: 20px;
  background-color: #1f9fc4;
  color: white;
}
</style>
