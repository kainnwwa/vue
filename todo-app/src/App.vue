<template>
  <div>
    <form @submit.prevent="addTodo">
      <input 
        v-model="newTodoText" 
        type="text" 
        placeholder="ЧЕэто?"
      />
      <button type="submit">Добавить</button>
    </form>

    <ul>
      <li v-for="задача in todos" :key="задача.id">
        {{ задача.id }} - {{ задача.text }}
      </li>
    </ul>

    <!-- <p>Счетчик: {{ nextId }}</p>
    <input v-model="newTodoText" />
    <div v-for="задача in todos" :key="задача.id">
      {{ задача.id }} - {{ задача.text }}
    </div>-->
    
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
