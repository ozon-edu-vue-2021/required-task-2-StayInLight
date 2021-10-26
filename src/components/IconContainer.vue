<template>
  <div class="container">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'IconContainer',
};
</script>

<style scoped>
.container {
  width: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
