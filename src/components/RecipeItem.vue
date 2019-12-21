<template lang="html">
<li v-on:mouseover="handleMouseOver" v-on:mouseleave="handleMouseLeave">{{recipe.label}}
  <recipe-item-cooking-time  :hoverRecipe="hoverRecipe" ></recipe-item-cooking-time>
</li>
</template>

<script>
import RecipeItemCookingTime from './RecipeItemCookingTime.vue'

export default {
  name: 'recipe-item',
  props: ['recipe'],
  data(){
    return{
    hoverRecipe: null
  }
  },
  components: {
    "recipe-item-cooking-time": RecipeItemCookingTime
  },
  methods: {
    handleMouseOver: function(){
       this.hoverRecipe = this.recipe
    },
    handleMouseLeave: function(){
       this.hoverRecipe = null
    },
  }

}
</script>

<style lang="css" scoped>
</style>
