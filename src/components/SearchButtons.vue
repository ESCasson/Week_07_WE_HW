<template lang="html">
  <div class="">
    <label for="">Enter Search Ingredient: </label>
    <input type="text" v-model="searchIngredient" placeholder="chicken">
    <label for="">Enter a Excluded Ingredient: </label>
    <input type="text" v-model="excludeIngredient" placeholder="">
    <button v-on:click="handleClick">Search</button>
  </div>

</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'search-buttons',
  data()  {
    return {
      "searchIngredient": null,
      "excludeIngredient": null,
    }
  },
  methods: {
    handleClick: function() {
      eventBus.$emit('search-ingredient', this.searchIngredient)
      eventBus.$emit('exclude-ingredient', this.excludeIngredient)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
