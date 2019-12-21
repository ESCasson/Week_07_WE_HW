<template lang="html">
  <div class="favRecipesList">
    <h3>Favorite recipes</h3>
    <ul>
      <favorite-recipe-item v-for="(recipe, index) in favRecipes" :recipe='recipe' :key='index'>
      </favorite-recipe-item>
    </ul>

  </div>
</template>

<script>
import FavoriteRecipeItem from './FavoriteRecipeItem.vue'
export default {
  name: 'fav-recipes-list',
  props: ['favRecipes'],
components: {
  'favorite-recipe-item': FavoriteRecipeItem,
}
}
</script>

<style lang="css" scoped>
</style>
