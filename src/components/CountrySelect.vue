<template lang="html">
  <div>
    <select v-model="country" @change="handleChange()">
      <option default disabled>Select a country</option>
      <option v-for="(country, index) in countries" :value="country" :key="index">{{country.name}}</option>
    </select>
  </div>
</template>

<script>
import {eventBus} from '../main.js';
export default {
  name: 'country-select',
  data(){
    return{
      country: null
    }
  },
  props: ['countries'],
  methods : {
    handleChange(){
      eventBus.$emit('country-selected', this.country);
    }
}
}
</script>

<style lang="css" scoped>
</style>
