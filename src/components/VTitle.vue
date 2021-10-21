<template>
<component class="v-title"  :is="tag">
  <slot />
</component>
  <!-- <div>
    VTitle
  </div> -->
</template>

<script>
export default {
  props: {
    tag: {
      type: String,
      default: 'h1'
    }
  }
}
</script>

<style lang="scss" scoped>
.v-title {
  font-size: 48px;
}
</style>
