<script>
export default {
  data() {
    return {
      name: "John Doe",
      status: false,
      tasks: ["task One", "task Two", "Task Three"],
      link: "https://google.com",
    };
  },

  methods: {
    toggleStatus() {
      if (this.status == true) {
        this.status = false;
      } else if (this.status == false) {
        this.status = true;
      }
    },
  },
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status">User is active</p>
  <p v-else>User is inactive</p>
  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <!--: this to say it is dynamic variable-->
  <a :href="link">Go To google</a>
  <br />
  <button @click="toggleStatus">Change Status</button>
</template>
