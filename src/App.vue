<script setup lang="ts">
import { computed, ref } from "vue";
import TaskForm from "./components/TaskForm.vue";
import type { Task } from "./types";
import TaskList from "./components/TaskList.vue";

const message = ref("Hello World")
const tasks = ref<Task[]>([])

const totalDone = computed(() => tasks.value.reduce((total, tasks) => tasks.done ? total + 1 : total, 0))

function addTask(newTask: string) {
  tasks.value.push({
    id: crypto.randomUUID(),
    title: newTask,
    done: false
  })
}

function toggleDone(id: string) {
  const task = tasks.value.find((task) => task.id == id)

  if (task) {
    task.done = !task.done
  }
}

function removeTask(id: string) {
  const index = tasks.value.findIndex((task) => task.id == id)

  if (index !== -1) {
    tasks.value.splice(index, 1)
  }
}

</script>

<template>
  <main>
    <h1>{{ message }}</h1>

    <TaskForm @add-task="addTask" />
    <h3 v-if="tasks.length <= 0">Add a task to get started.</h3>
    <h3 v-else>{{ totalDone }} / {{ tasks.length }} tasks completed</h3>
    <TaskList :tasks @toggle-done="toggleDone" @remove-task="removeTask" />
  </main>
</template>

<style scoped>
main {
  color: red;
  max-width: 800px;
  margin: 1rem auto;
}
</style>
