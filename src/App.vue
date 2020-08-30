<template>
  <div id="app">
    <Todoist />
  </div>
</template>

<script>
import Todoist from './components/Todoist.vue'

export default {
  name: 'App',
  components: {
    Todoist
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
