<template lang="html">
  <div class="seat"></div>
</template>

<script>
  export default {
    name: 'seat'
  }
</script>

<style lang="css" scoped>
  .seat {
    cursor: pointer;
    width: 35px;
    height: 50px;
    margin-top: -32px;
    border-radius: 7px;
    margin-bottom: 10px;
    transform: skew(20deg);
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
    background: linear-gradient(to top, #761818, #761818, #761818, #761818, #761818, #B54041,  #F3686A);
  }
  .seat:hover::before {
    content: '';
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    border-radius: 7px;
  }
  .seat.active {}
  .seat.active::before {
    content: '';
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.6);
    border-radius: 7px;
  }
</style>
