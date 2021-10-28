<template>
  <div
    class="node__content"
    :class="{ selected: path === getSelectedPath() }"
    @click="setSelectedPath(path)"
  >
    <icon-container>
      <font-awesome-icon icon="link" />
    </icon-container>
    {{ name }}
  </div>
</template>

<script>
import IconContainer from './IconContainer.vue';

export default {
  components: { IconContainer },
  name: 'LinkItem',
  inject: ['getSelectedPath', 'setSelectedPath'],
  props: {
    name: {
      type: String,
      required: true,
    },
    path: {
      type: String,
      default: '',
    },
  },
};
</script>

<style scoped >
@import "../main.css";
</style>
