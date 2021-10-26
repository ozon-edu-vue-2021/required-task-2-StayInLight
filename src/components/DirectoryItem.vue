<template>
  <div class="directory">
    <div
      class="node__content"
      @click="toggleChildren"
    >
      <button
        v-if="node.type === 'directory'"
        class="button"
      >
        <font-awesome-icon :icon="getIconMap.angle" />
      </button>
      <icon-container>
        <font-awesome-icon :icon="getIconMap.folder" />
      </icon-container>
      {{ node.name }}
    </div>
    <link-item
      v-if="node.type === 'link'"
      :name="node.name"
      :path="path"
    />
    <file-item
      v-else-if="node.type === 'file'"
      :name="node.name"
      :path="path"
    />
    <div v-if="hasChildren && showChildren" >
      <directory
        v-for="(child, index) in node.contents"
        :key="`${child.name}${child.type}${index}`"
        :node="child"
        :path="`${path}/${child.name}`"
      />
    </div>
  </div>
</template>

<script>
import FileItem from './FileItem.vue';
import IconContainer from './IconContainer.vue';
import LinkItem from './LinkItem.vue';

export default {
  name: 'Directory',
  components: {
    IconContainer,
    FileItem,
    LinkItem,
  },
  props: {
    node: {
      type: Object,
      required: true,
    },
    path: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      showChildren: false,
    };
  },
  computed: {
    hasChildren() {
      const { contents } = this.node;
      return contents && contents.length > 0;
    },
    getIconMap() {
      const { showChildren, hasChildren } = this;

      return showChildren && hasChildren ? {
        angle: 'angle-down',
        folder: 'folder-open',
      } : {
        angle: 'angle-right',
        folder: 'folder',
      };
    },
  },
  methods: {
    toggleChildren() {
      this.showChildren = !this.showChildren;
    },
  },
};
</script>

<style scoped >
@import "../main.css";

.directory {
  margin-left: 28px;
}

.button {
  cursor: pointer;
  width: 20px;
  border: none;
  background-color: transparent;
}
</style>
