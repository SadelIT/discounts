<template>
  <discount></discount>
</template>

<script>
import Discount from './components/discounts.vue'

export default {
  name: 'App',
  components: {
    Discount
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
