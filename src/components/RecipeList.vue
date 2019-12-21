<template lang="html">
<div class="">
  <h1>Recipe List</h1>
  <ul>
    <recipe-item v-for="(recipe, index) in recipes" :recipe="recipe.recipe" :key="index"></recipe-item>

  </ul>
</div>

</template>

<script>
import RecipeItem from './RecipeItem.vue'
export default {
  name: 'recipe-list',
  props: ['recipes'],
  components: {
    "recipe-item": RecipeItem
  }

}
</script>

<style lang="css" scoped>
</style>
