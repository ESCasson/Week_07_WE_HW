<template>
  <div id="app">
    <h1>This Page</h1>
    <search-buttons></search-buttons>
    <recipe-list :recipes='recipes'></recipe-list>
    <recipe-details :recipeDetails='recipeDetails'></recipe-details>
  </div>
</template>

<script>
import RecipeList from './components/RecipeList.vue';
import SearchButtons from './components/SearchButtons.vue';
import {eventBus} from './main.js';
import RecipeDetails from './components/RecipeDetails.vue';

export default {
  name: 'app',

  components:{
    "recipe-list": RecipeList,
    "search-buttons": SearchButtons,
    "recipe-details": RecipeDetails
  },

  data(){
    return {
      recipes: [],
      searchIngredient: 'chicken',
      excludeIngredient: null,
      recipeDetails: null
    }
  },

  methods: {
    newfetch: function(){
      fetch(`https://api.edamam.com/search?q=${this.searchIngredient}&exclude=${this.excludeIngredient}&app_id=bcd54046&app_key=4388baf0907a4ec0730de331e147ec1d&from=0&to=20`)
      .then(res => res.json())
      .then(recipes => this.recipes = recipes.hits)
    }
  },
  mounted(){
    fetch(`https://api.edamam.com/search?q=${this.searchIngredient}&app_id=bcd54046&app_key=4388baf0907a4ec0730de331e147ec1d&from=0&to=20`)
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

    }


    }



</script>

<style>

</style>
