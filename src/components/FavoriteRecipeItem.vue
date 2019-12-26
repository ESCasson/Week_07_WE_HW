<template lang="html">
  <div class="">
    <li>{{recipe.recipe.label}}</li>
    <button type="button" name="button" v-on:click="removeItem">Remove from Favorites</button>
  </div>

<!-- add a made and then differculty input item -->
</template>

<script>
import { eventBus } from '../main.js';
export default {
  name: 'favorite-recipe-item',
  props: ['recipe'],
  methods: {
    removeItem: function(){
        eventBus.$emit('remove-recipe', this.recipe)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
