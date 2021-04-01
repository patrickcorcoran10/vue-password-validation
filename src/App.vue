<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <PasswordInput/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import PasswordInput from './components/PasswordInput'
export default {
  name: 'App',
  components: {
    // HelloWorld,
    PasswordInput
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
