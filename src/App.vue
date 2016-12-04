<template>
  <div id="app">
    <img src="./assets/fridge.svg">
    <Inventory></Inventory>
  </div>
</template>

<script>
import Inventory from './components/Inventory'

export default {
  name: 'app',
  components: {
    Inventory
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
img {
  width: 20%;
}
</style>
