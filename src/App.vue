<template>
  <div id="app">
    <Header />
    <div id='nav'>
        <router-link to="/">Home</router-link>
        <router-link to="/about"> About </router-link>
    </div>
    <router-view />
  </div>
</template>
]

<script>
import Header from './components/Header';
export default {
  // name, methods, props, computed,data, el etc. can be exported
  name: 'App',
  components: {
    Header
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
