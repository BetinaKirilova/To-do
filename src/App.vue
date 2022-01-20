<template>
  <div class="main-wrap">
    <NewTaskPopup v-if="popupVisible" @task="getTask" @close="closePopup" />
    <TaskContainer :tasks="tasks" :title="listTitle" />
    <div class="add" @click="add()">+</div>
    <div
      class="options"
      v-for="option in listOptions"
      :key="option.name"
      @click="getList(option.name)"
      :style="'background-color: ' + option.color"
    >
      <p>{{ option.name }}</p>
    </div>
  </div>
</template>

<script>
import TaskContainer from "./components/TaskContainer.vue";
import NewTaskPopup from "./components/NewTaskPopup.vue";

export default {
  name: "App",
  components: {
    TaskContainer,
    NewTaskPopup,
  },
  data() {
    return {
      tasks: [],
      workTasks: [],
      groceryTasks: [],
      schoolTasks: [],
      popupVisible: false,
      listOptions: [
        { name: "Work", color: "#116F8B" },
        { name: "Groceries", color: "#1F9FC4" },
        { name: "School", color: "#93CBDB" },
      ],
      listTitle: "Work",
    };
  },

  methods: {
    add() {
      this.popupVisible = true;
    },
    getTask(value) {
      switch (this.listTitle) {
        case "Work":
          this.workTasks.push(value);
          break;
        case "Groceries":
          this.groceryTasks.push(value);
          break;
        case "School":
          this.schoolTasks.push(value);
          break;
      }
      this.getList(this.listTitle);
    },
    closePopup() {
      this.popupVisible = false;
    },
    getList(option) {
      switch (option) {
        case "Work":
          this.listTitle = "Work";
          this.tasks = this.workTasks;
          break;
        case "Groceries":
          this.listTitle = "Groceries";
          this.tasks = this.groceryTasks;
          break;
        case "School":
          this.listTitle = "School";
          this.tasks = this.schoolTasks;
          break;
      }
    },
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  font-family: sans-serif;
}

html {
  background-color: #e3efff;
}

.options {
  position: relative;
  top: 200px;
  left: 60%;
  width: 350px;
  height: 55px;
  margin-top: 20px;
  font-size: 30px;
  text-align: center;
  padding-top: 30px;
  border-radius: 68px;
  color: white;
}

.add {
  position: absolute;
  left: 760px;
  top: 650px;
  height: 100px;
  width: 100px;
  background-color: #116f8b;
  border-radius: 50%;
  text-align: center;
  font-size: 85px;
  color: white;
}
</style>
