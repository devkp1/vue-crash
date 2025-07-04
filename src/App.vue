<script>
export default {
  data() {
    return {
      name: "john Doe",
      status: "",
      tasks: ["task 1", "task 2", "task 3", "task 4"],
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
</template>

<style scoped>
h1 {
  /* text-align: center; */
}
</style>
