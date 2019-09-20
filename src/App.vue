<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <HelloWorld/> -->
    <!-- <Slider/> -->
    <!-- <LeftNav/> -->
    <Search/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Slider from './components/slider'
import LeftNav from './components/leftNav'
import Search from './components/search'
export default {
  name: 'App',
  components: {
    HelloWorld,
    Slider,
    LeftNav,
    Search
  }
}
</script>

<style>
#app {
  /* font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}
</style>
