<template>
  <div id="app">
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <RegIstration/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import RegIstration from "./components/RegIstration.vue"

export default {
  name: 'App',
  components: {
    RegIstration
  }
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
