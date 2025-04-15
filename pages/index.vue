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
  <h1>Список задач</h1>
  <TaskForm @add="addTask" />
  <TaskList :tasks="tasks" :onDelete="deleteTask" />
</template>