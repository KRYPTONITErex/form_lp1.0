<template>
  <h2>Hello eveyone</h2>

  <Signup></Signup>
</template>

<script>

import Signup from './components/Signup'
export default {
  name: 'App',
  components: {
    Signup,
    
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
  background-color: #dee0e1;
  margin: 0;
}
</style>
