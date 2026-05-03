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
        <input type="checkbox" v-model="задача.completed" />
        <span :class="{ completed: задача.completed }">
          {{ задача.id }} - {{ задача.text }}
        </span>
        <button @click="deleteTodo(задача)">Удалить</button>
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

function addTodo() {
  if (newTodoText.value.trim() === '') {
    alert('Введите текст задачи!')
    return
  }
  
  todos.value.push({
    id: nextId++,
    text: newTodoText.value,
    completed: false
  })
  
  newTodoText.value = ''
}
function deleteTodo(todo) {
  todos.value = todos.value.filter(t => t.id !== todo.id)
}
</script>

<style scoped>
.completed {
  text-decoration: line-through;
  color: gray;
}

li {
  margin: 10px 0;
  list-style: none;
}

button {
  margin-left: 10px;
  background-color: #520707;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 2px 8px;
  cursor: pointer;
}

input[type="text"] {
  padding: 5px;
  margin-right: 5px;
}
</style>
