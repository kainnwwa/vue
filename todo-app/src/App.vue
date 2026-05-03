<template>
  <div>
    <p>Счетчик: {{ nextId }}</p>
    <input v-model="newTodoText" />
    <div v-for="задача in todos" :key="задача.id">
      {{ задача.id }} - {{ задача.text }}
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

let nextId = 3
const newTodoText = ref('')
const todos = ref([
  { id: 1, text: 'Задача 1', completed: false },
  { id: 2, text: 'Задача 2', completed: false }
])
</script>
