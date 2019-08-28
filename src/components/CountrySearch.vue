<template lang="html">
  <div>
    <label for="country-search">Search for a country: </label>
    <input id="country-search" @input="onInput" type="text" v-model="countryName">
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'country-search',
  props: ['countries'],
  data() {
    return {
      countryName: ""
    }
  },
  methods: {
    onInput() {
      for (let country of this.countries) {
        if (country.name.indexOf(this.countryName) > -1) {
          return eventBus.$emit('country-selected', country)
        }
      }
    }
  }
}
</script>

<style lang="css" scoped>
</style>
