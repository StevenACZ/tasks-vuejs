<script setup lang="ts">
import { ref } from "vue";

const emit = defineEmits<{
  addTask: [newTask: string]
}>()

const error = ref("")
const newTask = ref("")

function formSubmitted() {
  if (newTask.value) {
    emit("addTask", newTask.value)
    newTask.value = ""
    error.value = ""
  } else {
    error.value = "Empty"
  }
}
</script>

<template>
  <form @submit.prevent="formSubmitted">
    <label>
      New Task
      <input
        v-model="newTask"
        type="text"
        name="newTask"
        :aria-invalid="!!error || undefined"
        @input="error = ''"
      >
      <small v-if="error" id="invalid-helper">
        Please provide a valid value!
      </small>
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
