<template>
  <div id="app">
    <cinema />
  </div>
</template>

<script>
  import Cinema from './components/Cinema.vue'

  export default {
    name: 'app',
    components: {
      Cinema
    }
  }
</script>

<style lang="css">
  body {
      width: 100%;
      height: 100%;
      margin: 60px;
      background-color: black;
  }
</style>
