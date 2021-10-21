<template>
<li class="v-todo-item">
  <button>Check</button>
  <span>{{ text }}</span>
  <button>Supprimer</button>
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
  setup () {
    return {}
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
