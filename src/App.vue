<template>
  <div id="app">
    <h1 style="margin: 0">Calculator</h1>
      <small>by Michael Sosa</small>
      <br>
    <img alt="Vue logo" style="width: 21px;" src="./assets/logo.png">
    <Calculator/>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'app',
  components: {
    Calculator
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
