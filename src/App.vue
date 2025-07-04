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
</template>

<style scoped>
h1 {
  /* text-align: center; */
}
</style>
