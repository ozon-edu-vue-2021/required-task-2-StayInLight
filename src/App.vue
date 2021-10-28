<template>
  <div id="app">
    <directory-item
      :node="treeData"
      :path="treeData.name"
    />
    <app-path :path="selectedPath"/>
  </div>
</template>

<script>
import treeData from '../public/static/node_modules.json';
import AppPath from './components/AppPath.vue';
import DirectoryItem from './components/DirectoryItem.vue';

export default {
  name: 'App',
  provide() {
    return {
      getSelectedPath: this.getSelectedPath,
      setSelectedPath: this.setSelectedPath,
    };
  },
  data() {
    return {
      treeData,
      selectedPath: '',
    };
  },
  components: {
    DirectoryItem,
    AppPath,
  },
  methods: {
    setSelectedPath(newSelectedPath) {
      let pathToSet = '';
      if (this.selectedPath !== newSelectedPath) {
        pathToSet = newSelectedPath;
      }
      this.selectedPath = pathToSet;
    },
    getSelectedPath() {
      return this.selectedPath;
    },
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  max-width: 1200px;
  margin: 30px auto 0;
  display: grid;
  grid-template-columns: 3fr 2fr;
  border: 1px solid #2c3e50;
  border-radius: 6px;
  padding: 8px;
}
</style>
