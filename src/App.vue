<script setup lang="ts">
import { ref } from "vue";
import TaskForm from "./components/TaskForm.vue";

const message = ref("Hello World")
</script>

<template>
  <main>
    <h1>{{ message }}</h1>

    <TaskForm ></TaskForm>
  </main>
</template>

<style scoped>
main {
  color: red;
  max-width: 800px;
  margin: 1rem auto;
}
</style>
