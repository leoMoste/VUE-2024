<script setup>
import { ref, onMounted } from "vue";

// ref ==> UseState() in react
const name = ref("John Doe");

const status = ref(false);
const tasks = ref(["task One", "task Two", "Task Three"]);
const newTask = ref("");

const link = ref("https://google.com");

const toggleStatus = () => {
  if (status.value == true) {
    status.value = false;
  } else if (status.value == false) {
    status.value = true;
  }
};

const addTask = () => {
  if (newTask.value.trim() != "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};

// Lifecycle Methods: there is more search about them
onMounted(async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await response.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log("Error fetching tasks");
  }
});
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status">User is active</p>
  <p v-else>User is inactive</p>
  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span> {{ task }}</span>
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>
  <!--: this to say it is dynamic variable-->
  <a :href="link">Go To google</a>
  <br />
  <button @click="toggleStatus">Change Status</button>
</template>
