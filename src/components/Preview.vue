<template lang="html">
    <div class="seats-preview" v-if="selectedSeats.length">
      <span v-for="(seat, index) in selectedSeats" :key="`selected-seat-${seat}`">{{ seat }}</span>
      <h5 v-if="toManySeatsSelected">To many seats selected.</h5>
      <button @click="startReservation" :class="{'disabled': toManySeatsSelected}" type="button">Reserve selected seats</button>
    </div>
</template>

<script>
  export default {
    name: 'preview',
    props: {
      selectedSeatsProp: {
        type: Array,
        required: true
      }
    },
    computed: {
      toManySeatsSelected () {
        return this.selectedSeats.length > this.selectedSeatsMax
      }
    },
    data () {
      return {
        selectedSeats: [],
        selectedSeatsMax: 5
      }
    },
    created () {
      this.selectedSeats = this.selectedSeatsProp
    },
    watch: {
      selectedSeatsProp(value) {
        this.selectedSeats = value
      }
    },
    methods: {
      startReservation () {
        this.$emit('start-reservation', true)
      }
    }
  }
</script>

<style lang="css" scoped>
  .seats-preview {
    left: 0;
    right: 0;
    top: -600px;
    width: 100%;
    color: white;
    border-radius: 5px;
    position: absolute;
    border: 1px solid #fff;
    padding: 30px 20px;
  }
  span {
    display: inline-block;
    margin: 0 10px 0 0;
  }
  h5 {
    margin: 20px 0 0;
    color: red;
  }
  /* button was here, moved to the global, remember */
</style>
