<template>
  <div id="app">
     <Register/>
    <Login/> 
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Login from './components/login.vue';
import Register from './components/register.vue';

export default {
  name: 'App',
  components: {
    Register,
    Login
    
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
