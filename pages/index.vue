<script setup lang="ts">
import { ref } from 'vue'
import type { Task } from '~/types/task'
import TaskList from '~/components/TaskList.vue'
import TaskForm from '~/components/TaskForm.vue'

const tasks = ref<Task[]>([])
let nextId = 1

function addTask(title: string) {
  tasks.value.push({ id: nextId++, title })
}

function deleteTask(id: number) {
  tasks.value = tasks.value.filter(task => task.id !== id)
}
</script>

<template>
  <div class="max-w-xl mx-auto p-4">
    <h1 class="text-3xl font-bold mb-4 text-center text-blue-600">Список задач</h1>
    <TaskForm @add="addTask" />
    <TaskList :tasks="tasks" :onDelete="deleteTask" />
  </div>
</template>