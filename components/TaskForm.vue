<script setup lang="ts">
import { ref } from 'vue'

const newTask = ref('')
const emit = defineEmits<{
  (e: 'add', taskTitle: string): void
}>()

function handleSubmit() {
  if (newTask.value.trim()) {
    emit('add', newTask.value)
    newTask.value = ''
  }
}
</script>

<template>
  <form @submit.prevent="handleSubmit" class="max-w-md mx-auto p-4 bg-white shadow-lg rounded-lg">
    <div class="mb-4">
      <label for="task" class="block text-sm font-medium text-gray-700">Введите задачу</label>
      <input
        v-model="newTask"
        id="task"
        type="text"
        placeholder="Новая задача"
        class="mt-2 w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
      />
    </div>
    <button
      type="submit"
      class="w-full p-2 bg-blue-600 text-white rounded-md hover:bg-blue-700 focus:ring-2 focus:ring-blue-500"
    >
      Добавить
    </button>
  </form>
</template>