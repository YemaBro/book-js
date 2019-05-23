<template>
  <div id="app">
    <router-view></router-view>
    <!--<SearchBox/>-->
  </div>
</template>

<script>
// import SearchBox from './components/SearchBox.vue'

export default {
  name: 'app',
  components: {
    // SearchBox
  }
}
</script>

<style>
  html, body, #app {
    padding: 0px;
    margin: 0px;
    height: 100%;
    width: 100%;
  }
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
