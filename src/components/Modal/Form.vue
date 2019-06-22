<template lang="html">
  <div>
    <div v-if="submitted" class="success">
      <h4>Great! Your tickets have been reserved.</h4>
    </div>
    <form v-else @submit.prevent="submit" novalidate>
        <input v-model="name" placeholder="Write your name"/>
        <input v-model="surname" placeholder="Write your name"/>
        <select v-model="payment">
          <option selected="true" disabled="disabled">Select payment type</option>
          <option v-for="(type, index) in paymentTypes" :key="index">{{ type }}</option>
        </select>
        <button :class="{'disabled': validate}" class="reversed" type="submit">Reserve seats</button>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'reservation-form',
    computed: {
      validate () {
        return !this.name || !this.surname || !this.payment
      }
    },
    data () {
      return {
        name: '',
        surname: '',
        payment: '',
        paymentTypes: [
          'cash',
          'credit card'
        ],
        submitted: false
      }
    },
    methods: {
      submit () {
        if (!this.validate) {
          this.$nextTick(() => {
            this.submitted = true
            setTimeout(() => {
              this.$emit('close-modal', true)
            }, 3000)
          })
        }
      }
    }
  }
</script>

<style lang="css" scoped>
  input, select {
    width: 100%;
    margin: 8px 0;
    color: black;
    font-size: 20px;
    padding: 12px 20px;
    box-sizing: border-box;
    border: 1px solid #ccc;
    background-color: white;
    border-radius: 5px;
    appearance: none;
  }
  select::after {
    content: '';
    top: 10px;
    right: 10px;
    width: 20px;
    height: 20px;
    position: absolute;
    display: inline-block;
    background-repeat: no-repeat;
    background-image: url('/assets/arrow.png')
  }
  h4 {
    color: green;
    /* text-align: center; */
  }
</style>
