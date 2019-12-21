<template lang="html">
  <div class="" v-if='recipeDetails'>
    <h1>{{recipeDetails.label}}</h1>
    <img :src="recipeDetails.image" alt="">
    <h2>Ingredients and Amounts</h2>
      <li v-for='item in recipeDetails.ingredientLines'>{{item}}</li>
      <a :href="recipeDetails.url">Link to the Recipe</a>

  </div>
</template>

<script>
export default {
  name: 'recipe-details',
  props:['recipeDetails']
}
</script>

<style lang="css" scoped>
</style>
