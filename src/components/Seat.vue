<template lang="html">
  <div class="seat" @click="selectSeat" :class="{'active': selected, 'disabled': disabled}"></div>
</template>

<script>
  import { mapGetters } from 'vuex'

  export default {
    name: 'seat',
    props: {
      seatProp: {
        type: String,
        default: ''
      }
    },
    computed: {
      ...mapGetters([
        'getReservedSeats'
      ])
    },
    data () {
      return {
        selected: false,
        disabled: false
      }
    },
    created () {
      this.checkReservations()
      this.$store.subscribe((mutation, state) => {
        if (mutation.type === 'RESERVE_SEATS') this.checkReservations()
      })
    },
    methods: {
      selectSeat () {
        if (!this.disabled) {
          this.selected = !this.selected
          this.$emit('seat-selected', {
            id: this.seatProp,
            type: this.selected ? 'add' : 'remove'
          })
        }
      },
      checkReservations () {
        this.getReservedSeats.map(seat => {
          if (seat === this.seatProp) this.disabled = true
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
  .seat.active::before, .seat.disabled::before {
    content: '';
    top: 0;
    width: 100%;
    height: 100%;
    position: absolute;
    border-radius: 7px;
    background: rgba(255, 255, 255, 0.6);
  }
  .seat.disabled {
    pointer-events: none;
  }
  .seat.disabled::before {
    background: rgba(255,138,0,1);
  }
</style>
