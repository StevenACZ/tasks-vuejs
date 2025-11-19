<script setup lang="ts">
import { ref } from "vue";

const newTask = ref("")

function formSubmitted() {
  console.log(newTask.value)
}
</script>

<template>
  <form @submit.prevent="formSubmitted">
    <label>
      New Task
      <input v-model="newTask" type="text" name="newTask">
    </label>

    <div class="button-container">
      <button>Add</button>
    </div>
  </form>
</template>

<style scoped>
.button-container {
  display: flex;
  justify-content: end;
}
</style>
