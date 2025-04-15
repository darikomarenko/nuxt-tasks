<script setup lang="ts">
import type { Task } from '~/types/task'

defineProps<{
  tasks: Task[]
  onDelete: (id: number) => void
}>()
</script>

<template>
  <ul class="space-y-4">
    <li
      v-for="task in tasks"
      :key="task.id"
      class="flex justify-between items-center p-4 bg-white shadow-sm rounded-lg"
    >
      <span class="text-lg font-semibold text-gray-800">{{ task.title }}</span>
      <button
        @click="onDelete(task.id)"
        class="px-3 py-1 text-sm text-white bg-red-600 rounded-md hover:bg-red-700 focus:ring-2 focus:ring-red-500"
      >
        Удалить
      </button>
    </li>
  </ul>
</template>
