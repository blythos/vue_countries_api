<template lang="html">
<div>
  <h3>Country: {{country.name}}</h3>
  <p>Population: {{country.population}}</p>
  <p>Capital: {{country.capital}}</p>
  <p><img :src="country.flag" class="flag-image"></p>
  <p>Languages spoken:</p>
  <ul>
    <li v-for="(language, index) in country.languages" :key="index">{{language.name}}</li>
  </ul>

</div>
</template>

<script>

export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
.flag-image {
  width: 100px;
}
</style>
