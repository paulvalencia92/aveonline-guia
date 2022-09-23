<template>
  <div id="app" class="m-0">
    <Jumbotron/>
    <Products/>
  </div>
</template>

<script>
import Products from './components/Products/Index'
import Jumbotron from './components/Jumbotron'

export default {
  name: 'App',
  components: {
    Products,
    Jumbotron
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
