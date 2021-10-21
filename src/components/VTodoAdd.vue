<template>
  <div>
    VTodoAdd
  </div>
</template>

<script>
export default {
  setup () {
    return {}
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
