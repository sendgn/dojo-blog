<template>
  <NavBar />
  <router-view />
</template>

<script>
  import NavBar from './components/NavBar.vue'

  export default {
    components: { NavBar }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }
  .error {
    color: crimson;
  }
  .layout {
    display: grid;
    grid-template-columns: 3fr 1fr;
    gap: 40px;
  }
</style>
