<template>
  <main>
    <VTitle tag="h3">Vue Todo List B3G2</VTitle>

    <VTodoAdd @add="addTodo"/>

    <ul class="todo-list">
      <VTodoItem
      v-for="(todo, index) in todos"
      :key="index"
      :text="todo.text"
      :status="todo.status"
      @check="toggleCheckStatus(index)"
      @remove="removeTodo(index)"
      />
      <p v-if="todos.length === 0">Il n'y a plus rien à faire</p>
    </ul>
  </main>
</template>

<script>
import VTitle from './components/VTitle'
import VTodoAdd from './components/VTodoAdd'
import VTodoItem from './components/VTodoItem'

import { ref, watch, onMounted } from 'vue'

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

    const addTodo = (text) => {
      const newTodo = {
        text,
        status: 'undone'
      }

      todos.value = [...todos.value, newTodo]
    }

    const removeTodo = (index) => {
      const temp = [...todos.value]

      temp.splice(index, 1)

      todos.value = temp
    }

    const toggleCheckStatus = (index) => {
      const temp = [...todos.value]

      // if (temp[index].status === 'done') {
      //   temp[index].status = 'undone'
      // } else {
      //   temp[index].status = 'done'
      // }

      temp[index].status = temp[index].status === 'undone'
        ? 'done'
        : 'undone'

      todos.value = temp
    }

    watch(todos, (val) => {
      window.localStorage.setItem('todos', JSON.stringify(val))
    })

    onMounted(() => {
      const todosFromStorage = window.localStorage.getItem('todos')
      if (todosFromStorage) {
        todos.value = JSON.parse(todosFromStorage)
      }
    })

    return {
      todos,
      toggleCheckStatus,
      removeTodo,
      addTodo
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
