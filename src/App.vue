<template>
  <div id="app">
    <NavBar />
    <Todoist />
  </div>
</template>

<script>
import Todoist from './components/Todoist.vue'
import NavBar from './components/NavBar.vue'

export default {
  name: 'App',
  components: {
    Todoist,
    NavBar
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
