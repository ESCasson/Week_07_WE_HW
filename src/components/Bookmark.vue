<template lang="html">
  <button v-on:click="handleClick" type="button" name="button">Bookmark Recipe</button>
</template>

<script>
import {eventBus} from '../main.js';
export default {
  name: 'bookmark',
  props: ['recipeDetails'],
  data(){
    return {
      bookmarkedBook: {
        recipe: null,
        made: false,
        differculty: null,
    }
  }

  },
  methods: {
    handleClick : function(){
    this.bookmarkedBook.recipe = this.recipeDetails
    eventBus.$emit('bookmarked-book', this.bookmarkedBook)
    this.bookmarkedBook = {recipe: null,
    made: false,
    differculty: null,}
  }
}
}
</script>

<style lang="css" scoped>
</style>
