<template lang="html">
  <div class="row" :class="sideProp">
    <seat v-for="(seat, index) in rowProp" :key="seat"/>
  </div>
</template>

<script>
  import Seat from './Seat.vue'

  export default {
    name: 'row',
    props: {
      rowProp: {
        type: Array,
        default: []
      },
      sideProp: {
        type: String,
        default: ''
      }
    },
    components: {
      Seat
    }
  }
</script>

<style lang="css" scoped>
  .row.left {
    transform: skew(-15deg);
    margin: 0 6px;
  }
  .row.right {
    transform: skew(-15deg);
    margin: 0 6px;
  }
</style>
