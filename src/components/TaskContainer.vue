<template>
  <div class="wrap">
    <div class="title">
      <p class="title-text">{{ title }}</p>
    </div>
    <div class="container">
      <div v-for="task in tasks" :key="task" class="tasks">
        <p class="task-name">{{ task }}</p>
        <div class="check" @click="checkTask(task)">
          <img
            src="@/assets/check.svg"
            alt=""
            class="check-icon"
            :class="task"
          />
        </div>
        <img
          src="@/assets/bin.svg"
          alt=""
          class="bin"
          @click="deleteTask(task)"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TaskContainer",
  props: {
    title: String,
    tasks: Array,
  },
  data() {
    return {};
  },
  methods: {
    checkTask(task) {
      let index = this.tasks.indexOf(task);
      console.log(index);
      document.getElementsByClassName("task-name")[index].style.textDecoration =
        "line-through";
      document.getElementsByClassName(task)[0].classList.add("show-check");
    },
    deleteTask(task) {
      let index = this.tasks.indexOf(task);
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
.title {
  position: absolute;
  top: 50px;
  left: 400px;
  width: 400px;
  height: 100px;
  background-color: #116f8b;
  border-radius: 40px;
  color: white;
}

.container {
  position: absolute;
  top: 200px;
  left: 400px;
  width: 400px;
  height: 500px;
  overflow-y: scroll;
  border: 5px solid #95bac6;
  border-radius: 40px;
  background-color: white;
}
.title-text {
  margin-top: 30px;
  font-size: 40px;
  text-align: center;
}

.tasks {
  margin-left: 20px;
  margin-top: 30px;
  width: 320px;
  height: 50px;
  text-align: center;
  display: inline-block;
  padding: 30px 20px 10px;
  background-color: #d5f5ff;
  border-radius: 20px;
}

.task-name {
  display: inline-block;
  position: relative;
  right: 70px;
  font-size: 25px;
}

.check {
  position: absolute;
  right: 90px;
  height: 20px;
  width: 20px;
  border: 1px solid black;
  display: inline-block;
}

.check-icon {
  visibility: hidden;
}

.show-check {
  visibility: visible;
}

.bin {
  position: absolute;
  right: 50px;
  display: inline-block;
}

::-webkit-scrollbar {
  padding: 1px;
  width: 7px;
  background: none;
}
</style>
