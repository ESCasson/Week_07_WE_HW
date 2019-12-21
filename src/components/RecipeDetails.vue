<template lang="html">
  <div class="" v-if='recipeDetails'>
    <h1>Details: {{recipeDetails.label}}</h1>
    <img :src="recipeDetails.image" alt="" />
    <li>Total Cooking Time: {{recipeDetails.totalTime}} min</li>
    <li>Number of Servings: {{recipeDetails.yield}}</li>
    <h2>Ingredients and Amounts</h2>
      <li v-for='item in recipeDetails.ingredientLines'>{{item}}</li>
      <a :href="recipeDetails.url" width="200px">Link to the Recipe</a>
      <bookmark :recipeDetails="recipeDetails"></bookmark>

  </div>
</template>

<script>
import Bookmark from './Bookmark.vue'
export default {
  name: 'recipe-details',
  props:['recipeDetails'],
  components: {
    "bookmark" : Bookmark
  }
}
</script>

<style lang="css" scoped>
</style>
