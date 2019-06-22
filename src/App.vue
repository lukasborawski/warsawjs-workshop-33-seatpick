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
      font-size: 20px;
      background-color: black;
      font-family: Arial, sans-serif;
  }
  h1, h2, h3, h4, h5, h6 {
    margin: 0px;
  }
  button {
    display: block;
    margin-top: 20px;
    border: 2px solid white;
    background-color: black;
    border-radius: 5px;
    color: white;
    padding: 14px 28px;
    font-size: 16px;
    cursor: pointer;
  }
  button.reversed {
    color: black;
    border-color: black;
    background-color: white;
  }
  button.disabled {
    opacity: .5;
    pointer-events: none;
  }
  button:hover {
    border-color: lime;
    color: lime;
  }
</style>
