<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <Sample/>
  </div>
</template>

<script>
import Sample from './components/Sample'

export default {
  name: 'App',
  components: {
    Sample
  }
}
</script>

<style>
body, body *{
  /* background: #333;
  color: #ccc; */
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
