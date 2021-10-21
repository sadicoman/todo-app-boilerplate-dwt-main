<template>
  <main>
    <VTitle tag="h3">Vue Todo List B3G2</VTitle>

    <VTodoAdd />

    <ul class="todo-list">
      <VTodoItem
      v-for="(todo, index) in todos"
      :key="index"
      :text="todo.text"
      />
    </ul>
  </main>
</template>

<script>
import VTitle from './components/VTitle'
import VTodoAdd from './components/VTodoAdd'
import VTodoItem from './components/VTodoItem'

import { ref } from 'vue'

export default {
  name: 'App',
  components: {
    VTodoItem,
    VTodoAdd,
    VTitle
  },

  setup () {
    const todos = ref([
      { text: 'faire un les courses', status: 'undone' },
      { text: 'Promenee le chien', status: 'undone' },
      { text: '...', status: 'undone' }
    ])

    return {
      todos
    }
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 500px;
  margin: 0 auto;
}

.todo-list {
  background: #ccc;
  border-radius: 5px;
  padding: 10px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
