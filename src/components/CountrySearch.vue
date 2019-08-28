<template lang="html">
  <div>
    <label for="country-search">Search for a country: </label>
    <input id="country-search" @change="onInput" type="text" v-model="countryName">
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
        if (this.countryName === country.name) {
          return eventBus.$emit('country-selected', country)
        }
      }
    }
  }
}
</script>

<style lang="css" scoped>
</style>
