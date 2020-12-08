<template>
  <div id="app">
    <RandomCat msg="Random GIF Cat"/>
  </div>
</template>

<script>
import RandomCat from './components/RandomCat.vue'

export default {
  name: 'App',
  components: {
    RandomCat
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body{
  background-color: lightblue;
}
</style>
