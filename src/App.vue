<script setup>
import { ref, computed } from 'vue'
import HeaderDate from './components/HeaderDate.vue'

const todosStore = ref([])
const todo = ref('')
const filter = ref('all')

const filteredTodosStore = computed(() => {
  if (filter.value === 'all') {
    return todosStore.value
  }

  if (filter.value === 'inProgress') {
    return todosStore.value.filter((todo) => !todo.done)
  }

  if (filter.value === 'finished') {
    return todosStore.value.filter((todo) => todo.done)
  }

  return todosStore.value
})

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
      <div class="filter-buttons-container">
        <button class="filter-btn" @click="filter = 'all'">Tout</button>
        <button class="filter-btn" @click="filter = 'inProgress'">En cours</button>
        <button class="filter-btn" @click="filter = 'finished'">Terminées</button>
      </div>
      <ul>
        <li
          v-for="(todo, index) in filteredTodosStore"
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
    <!-- <div class="progress_container">
      <div class="progress_outside">
        <div class="progress_inside"></div>
      </div>
    </div> -->
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
  padding: 2.5rem 1.25rem;
}

#app {
  width: 100%;
  display: flex;
  justify-content: center;
}
</style>

<style scoped>
.app-wrapper {
  width: 100%;
  max-width: 560px;
}

.input-row {
  display: flex;
  gap: 0;
  margin-bottom: 1.5rem;
  border-bottom: 1px solid #bbb8b2;
}

.filter-buttons-container {
  display: flex;
  flex-direction: row;
  gap: 8px;
  margin-bottom: 1.2rem;
}

.filter-btn {
  flex: 1;
  border: 1px solid #3a3a3a;
  border-radius: 6px;
  padding: 6px 4px;
  font-family: 'DM Mono', monospace;
  font-size: clamp(0.6rem, 2.5vw, 0.75rem);
  letter-spacing: 0.05em;
  color: #aaa9a2;
  background: transparent;
  cursor: pointer;
  transition:
    border-color 0.15s,
    color 0.15s;
}

.filter-btn:hover {
  border-color: #bbb8b2;
  color: #e4e4e4;
  opacity: 1;
}

.filter-btn.active {
  border-color: #bbb8b2;
  color: #e4e4e4;
}

input {
  flex: 1;
  background: transparent;
  border: none;
  outline: none;
  font-family: 'DM Mono', monospace;
  font-size: clamp(0.75rem, 3vw, 0.85rem);
  font-weight: 300;
  color: #bbb8b2;
  padding: 0.6rem 0;
  letter-spacing: 0.05em;
}

input::placeholder {
  color: #555551;
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
}

li {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  padding: 0.85rem 0;
  border-bottom: 1px solid #e0ddd818;
  cursor: pointer;
  transition: opacity 0.2s;
  /* zone de tap confortable sur mobile */
  min-height: 44px;
}

li:hover {
  opacity: 0.9;
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
  font-size: clamp(0.78rem, 3vw, 0.85rem);
  font-weight: 300;
  color: #e4e4e4;
  letter-spacing: 0.03em;
  transition: color 0.2s;
  word-break: break-word;
}

.delete-btn {
  font-size: 0.6rem;
  letter-spacing: 0.1em;
  color: #555551;
  padding: 0.4rem;
  opacity: 0;
  transition:
    opacity 0.15s,
    color 0.15s;
  /* toujours visible sur mobile (pas de hover) */
  min-width: 44px;
  text-align: right;
}

@media (hover: none) {
  .delete-btn {
    opacity: 1;
  }
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
  color: #555551;
}

.done_through .todo-check {
  color: #ffffff;
}
</style>
