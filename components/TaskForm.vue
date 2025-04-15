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
  <form @submit.prevent="handleSubmit">
    <input v-model="newTask" placeholder="Новая задача" />
    <button type="submit">Добавить</button>
  </form>
</template>
