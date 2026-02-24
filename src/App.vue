<script setup>
import { ref, computed } from 'vue'
import HeaderDate from './components/HeaderDate.vue'

const todosStore = ref([])
const todo = ref('')

function addTodo() {
  if (!todo.value) return
  todosStore.value.push({
    text: todo.value,
    done: false,
  })
  todo.value = ''
}

function deleteTodo(index) {
  todosStore.value.splice(index, 1)
}
</script>

<template>
  <HeaderDate />
  <div class="todo_form">
    <input v-model="todo" type="text" placeholder="Ajouter une tâche.." />
    <button @click="addTodo()">Ajouter</button>
    <ul>
      <li
        v-for="(todo, index) in todosStore"
        :key="index"
        @click="todo.done = !todo.done"
        :class="{ done_through: todo.done }"
      >
        {{ todo.text }} <button @click.stop="deleteTodo(index)">Sup</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.done_through {
  text-decoration: line-through;
}
</style>
