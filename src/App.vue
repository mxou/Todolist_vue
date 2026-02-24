<script setup>
import { ref } from 'vue'
import HeaderDate from './components/HeaderDate.vue'

const todosStore = ref([])
const todo = ref('')

function addTodo() {
  if (!todo.value) return
  todosStore.value.push({ text: todo.value, done: false })
  todo.value = ''
}

function deleteTodo(index) {
  todosStore.value.splice(index, 1)
}
</script>

<template>
  <div class="app-wrapper">
    <HeaderDate />
    <div class="todo_form">
      <div class="input-row">
        <input v-model="todo" type="text" placeholder="Nouvelle tâche…" @keyup.enter="addTodo" />
        <button @click="addTodo()">+</button>
      </div>
      <ul>
        <li
          v-for="(todo, index) in todosStore"
          :key="index"
          @click="todo.done = !todo.done"
          :class="{ done_through: todo.done }"
        >
          <span class="todo-check">{{ todo.done ? '✕' : '○' }}</span>
          <span class="todo-text">{{ todo.text }}</span>
          <button class="delete-btn" @click.stop="deleteTodo(index)">suppr</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Mono:wght@300;400&display=swap');

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: #1a1a1a;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  padding: 3rem 1rem;
}
</style>

<style scoped>
.app-wrapper {
  width: 100%;
  max-width: 480px;
}

.input-row {
  display: flex;
  gap: 0;
  margin-bottom: 2rem;
  border-bottom: 1px solid #bbb8b2;
}

input {
  flex: 1;
  background: transparent;
  border: none;
  outline: none;
  font-family: 'DM Mono', monospace;
  font-size: 0.85rem;
  font-weight: 300;
  color: #bbb8b2;
  padding: 0.6rem 0;
  letter-spacing: 0.05em;
}

input::placeholder {
  color: #bbb8b2;
}

button {
  background: transparent;
  border: none;
  cursor: pointer;
  font-family: 'DM Mono', monospace;
  color: #bbb8b2;
  font-size: 1.4rem;
  padding: 0 0.2rem;
  line-height: 1;
  transition: opacity 0.15s;
}

button:hover {
  opacity: 0.5;
}

ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0;
}

li {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  padding: 0.75rem 0;
  border-bottom: 1px solid #e0ddd8;
  cursor: pointer;
  transition: opacity 0.2s;
}

li:hover {
  opacity: 0.6;
}

.todo-check {
  font-family: 'DM Mono', monospace;
  font-size: 0.7rem;
  color: #aaa9a2;
  width: 1rem;
  flex-shrink: 0;
}

.todo-text {
  flex: 1;
  font-family: 'DM Mono', monospace;
  font-size: 0.85rem;
  font-weight: 300;
  color: #e4e4e4;
  letter-spacing: 0.03em;
  transition: color 0.2s;
}

.delete-btn {
  font-size: 0.6rem;
  letter-spacing: 0.1em;
  color: #ccc9c2;
  padding: 0;
  opacity: 0;
  transition:
    opacity 0.15s,
    color 0.15s;
}

li:hover .delete-btn {
  opacity: 1;
}
.delete-btn:hover {
  color: #c0392b !important;
  opacity: 1 !important;
}

.done_through .todo-text {
  text-decoration: line-through;
  color: #bbb8b2;
}

.done_through .todo-check {
  color: #ffffff;
}
</style>
