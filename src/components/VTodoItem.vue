<template>
<li
  class="v-todo-item" :class="{ 'is-checked': status === 'done' }"
>
  <button @click="sendCheckStatus">Check</button>
  <span>{{ text }}</span>
  <button @click="sendRemove">Supprimer</button>
</li>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      required: true
    },
    status: {
      type: String,
      required: true
    }
  },
  setup (props, { emit }) {
    const sendCheckStatus = () => {
      emit('check')
    }
    const sendRemove = () => {
      emit('remove')
    }
    return {
      sendCheckStatus,
      sendRemove
    }
  }
}
</script>

<style lang="scss" scoped>
.v-todo-item {
  padding: 8px;
  display: flex;
  justify-content: space-between;
  background: white;
  border-radius: 3px;
  background: antiquewhite;

  &.is-checked {
    filter: grayscale(1);

    span {
      text-decoration: line-through;
    }
  }
}
</style>
