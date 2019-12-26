<template>
  <div id="app">
    <h1>This Page</h1>
    <div class="recipes-container">
      <div class="recipeList-container">
        <search-buttons></search-buttons>
        <page-buttons :pageTo='pageTo' :pageFrom='pageFrom'></page-buttons>

        <recipe-list :recipes='recipes'></recipe-list>
      </div>
    <div class="recipe-details">
      <recipe-details :recipeDetails='recipeDetails'></recipe-details>
    </div>
  </div>
  <div class="favrecipes">
    <fav-recipes-list :favRecipes='favRecipes'></fav-recipes-list>
  </div>
  </div>
</template>

<script>
import RecipeList from './components/RecipeList.vue';
import SearchButtons from './components/SearchButtons.vue';
import {eventBus} from './main.js';
import RecipeDetails from './components/RecipeDetails.vue';
import FavRecipesList from './components/FavRecipesList.vue';
import PageButtons from './components/PageButtons.vue';

export default {
  name: 'app',

  components:{
    "recipe-list": RecipeList,
    "search-buttons": SearchButtons,
    "recipe-details": RecipeDetails,
    "fav-recipes-list": FavRecipesList,
    "page-buttons": PageButtons
  },

  data(){
    return {
      recipes: [],
      searchIngredient: 'chicken',
      excludeIngredient: null,
      recipeDetails: null,
      favRecipes: [],
      pageFrom: 0,
      pageTo: 12
    }
  },

  methods: {
    newfetch: function(){
      fetch(`https://api.edamam.com/search?q=${this.searchIngredient}&exclude=${this.excludeIngredient}&app_id=bcd54046&app_key=4388baf0907a4ec0730de331e147ec1d&from=${this.pageFrom}&to=${this.pageTo}`)
      .then(res => res.json())
      .then(recipes => this.recipes = recipes.hits)
    }
  },
  mounted(){
    fetch(`https://api.edamam.com/search?q=chicken&excluded=&app_id=bcd54046&app_key=4388baf0907a4ec0730de331e147ec1d&from=0&to=12`)
    .then(res => res.json())
    .then(recipes => this.recipes = recipes.hits)

    eventBus.$on('search-ingredient', (searchIngredient) =>{
      this.searchIngredient = searchIngredient
    this.newfetch()})

    eventBus.$on('exclude-ingredient', (excludeIngredient) =>{
      this.excludeIngredient = excludeIngredient
    this.newfetch()})

    eventBus.$on('recipe-details', (recipeDetails) =>{
      this.recipeDetails = recipeDetails
    })

    eventBus.$on('bookmarked-book', (bookmarkedBook) => {
      this.favRecipes.push(bookmarkedBook)
    })

    eventBus.$on('page-to', (pageTo) => {
      this.pageTo = pageTo
    })

    eventBus.$on('page-from', (pageFrom) => {
      this.pageFrom = pageFrom,
      this.newfetch()
    })

    }
  }

</script>

<style>
.recipes-container {
  display: flex;
}

</style>
