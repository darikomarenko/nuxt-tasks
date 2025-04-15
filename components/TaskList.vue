<script setup lang="ts">
import type { Task } from '~/types/task';

defineProps<{
  tasks: Task[]
  onDelete: (id: number) => void
}>()
</script>

<template>
  <ul>
    <li v-for="task in tasks" :key="task.id">
      {{ task.title }}
      <button @click="onDelete(task.id)">Удалить</button>
    </li>
  </ul>
</template>