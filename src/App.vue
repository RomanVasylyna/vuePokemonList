<template>
  <div id="app">
   <Pokemon/>
  </div>
</template>

<script>
// Importing Main Pokemon Container
import Pokemon from './components/Pokemon.vue'

export default {
  name: 'App',
  components: {
  Pokemon
  }
}
</script>

<style>

body{
margin: 0;
padding: 0;
box-sizing: border-box;
}

</style>
