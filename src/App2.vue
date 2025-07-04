<script>
export default {
  data() {
    return {
      name: "john Doe",
      status: "",
      tasks: ["task 1", "task 2", "task 3", "task 4"],
      link: "https://google.com/",
    };
  },
  methods: {
    toggleStatus() {
      if (this.status === "active") {
        this.status = "pending";
      } else if (this.status === "pending") {
        this.status = "inactive";
      } else {
        this.status = "active";
      }
      console.log("status:", this.status);
    },
  },
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is Active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else="status">User is Inactive</p>

  <p v-for="task in tasks">{{ task }}</p>
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
