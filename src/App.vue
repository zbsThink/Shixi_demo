<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <HelloWorld/> -->
    <!-- <Slider/> -->
    <!-- <LeftNav/> -->
    <!-- <Search/> -->
    <!-- <Upload/> -->
    <!-- <ScssStudy/> -->
    <FormTest/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Slider from './components/slider'
import LeftNav from './components/leftNav'
import Search from './components/search'
import Upload from './components/upload'
import ScssStudy from './components/scssStudy'
import FormTest from './components/formTest'
export default {
  name: 'App',
  components: {
    HelloWorld,
    Slider,
    LeftNav,
    Search,
    Upload,
    ScssStudy,
    FormTest
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
  margin:0;
  padding:0;
}
</style>
