<script>
export default {
  data() {
    return {
      name: "john Doe",
      status: "active",
    };
  },
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status">User is Active</p>
</template>

<style scoped>
h1 {
  /* text-align: center; */
}
</style>
