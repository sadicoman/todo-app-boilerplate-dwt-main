<template>
  <form class="v-todo-add">
    <div class="v-todo-add__input">
      <label for="add">Ajouter une todo : {{ text }}</label>
      <input type="text" name="add" v-model="text">
    </div>
    <button class="v-todo-add__button" @click.prevent="sendAdd">Ajouter</button>
  </form>
</template>

<script>
import { ref } from 'vue'

export default {
  setup (props, { emit }) {
    const text = ref('')

    const sendAdd = () => {
      if (text.value) {
        emit('add', text.value)
        text.value = ''
      }
    }
    return {
      text,
      sendAdd
    }
  }
}
</script>

<style lang="scss" scoped>
.v-todo-add {
  text-align: left;
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 20px;

  &__input {
    display: flex;
    flex-direction: column;
    width: 100%;

    input {
      height: 30px;
    }
  }

  &__button {
    height: 30px
  }
}
</style>
