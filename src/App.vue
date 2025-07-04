<script setup>
import { ref, onMounted } from "vue";

const name = ref("John Doe");
const status = ref("");
const tasks = ref(["task 1", "task 2", "task 3", "task 4"]);
const link = "https://google.com/";
const newTask = ref("add new task here."); // adding someting to show on the ui.

const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
  // console.log("status:", status.value);
};

const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};

onMounted(async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await response.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log("error fetching tasks.");
  }
});
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is Active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else="status">User is Inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" name="add-task" id="newTask" v-model="newTask" />
    <button type="submit">submit</button>
  </form>

  <h2>Tasks:</h2>
  <li v-for="(task, index) in tasks" :key="task">
    <span>
      {{ task }}
    </span>
    <button @click="deleteTask(index)">x</button>
  </li>
  <!-- <a v-bind:href="link">Click me to google.</a> -->
  <a :href="link">Click me to google.</a>
  <br />
  <!-- toggle status change-->
  <!-- <button v-on:click="toggleStatus">change status</button> -->
  <button @click="toggleStatus">change status</button>
</template>
<style scoped>
h1 {
  /* text-align: center; */
}
</style>
