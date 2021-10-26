<template>
  <div class="container">
    <div class="title">Path:</div>
    <ul
      class="list"
      v-if="getSplitedPath"
    >
      <li
        v-for="(pathItem, idx) in getSplitedPath"
        :key="`${pathItem}-${idx}`"
        class="list__item"
       >
        {{ pathItem }}
        <font-awesome-icon
          v-if="idx !== getSplitedPath.length - 1"
          icon="angle-right"
          class="list__item__separator"
        />
      </li>
    </ul>
    <span v-else>Nothing selected</span>
  </div>
</template>

<script>
export default {
  name: 'AppPath',
  props: {
    path: {
      type: String,
      required: true,
    },
  },
  computed: {
    getSplitedPath() {
      return this.path && this.path.split('/');
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

.title {
  font-weight: bold;
}

.list {
  list-style-type: none;
  display: flex;
  margin: 8px 0;
  padding: 0;
}

.list__item {
  display: flex;
  align-items: center;
}

.list__item__separator {
  padding: 0 6px;
}

</style>
