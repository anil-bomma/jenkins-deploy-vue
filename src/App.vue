<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Home msg="I LOVE VUE WITH DOCKER"/>
  <img alt="Docker logo" src="./assets/docker.png" style="width: 25%">
</template>

<script>
import Home from './components/Home.vue'

export default {
  name: 'App',
  components: {
    Home
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
</style>
