<template lang="html">
 <div>
   <h1>Countries</h1>

   <div class="main">
     <!-- <countries-list :countries='countries'></countries-list> -->
    <country-select :countries="countries"></country-select>
    <country-detail v-if="selectedCountry" :country="selectedCountry"></country-detail>

   </div>

 </div>
</template>

<script>
import CountryDetail from './components/CountryDetail.vue';
// import CountriesList from './components/CountriesList.vue';
import CountrySelect from './components/CountrySelect.vue';
import {eventBus} from './main.js';
export default {
  name: 'app',
  data(){

    return{
      countries: [],
      selectedCountry: null
    }
  },
   mounted(){
     fetch('https://restcountries.eu/rest/v2/all')
     .then(res => res.json())
     .then(data => this.countries = data)

     eventBus.$on('country-selected', (country) => {
       this.selectedCountry = country;
     })
   },
   components: {
     "country-select": CountrySelect,
     "country-detail": CountryDetail
   }
}

</script>

<style lang="css" scoped>
  .main {
    display: flex;
    justify-content: space-between;
  }
</style>
