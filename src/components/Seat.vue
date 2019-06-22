<template lang="html">
  <div class="seat" @click="selectSeat" :class="{'active': selected}"></div>
</template>

<script>
  export default {
    name: 'seat',
    props: {
      seatProp: {
        type: String,
        default: ''
      }
    },
    data () {
      return {
        selected: false
      }
    },
    methods: {
      selectSeat () {
        this.selected = !this.selected
        this.$emit('seat-selected', {
          id: this.seatProp,
          type: this.selected ? 'add' : 'remove'
        })
      }
    }
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
    top: 0;
    width: 100%;
    height: 100%;
    border-radius: 7px;
    position: absolute;
    background: rgba(0, 0, 0, 0.5);
  }
  .seat.active::before {
    content: '';
    top: 0;
    width: 100%;
    height: 100%;
    position: absolute;
    border-radius: 7px;
    background: rgba(255, 255, 255, 0.6);
  }
</style>
