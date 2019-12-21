<template lang="html">
<ul v-if='hoverRecipe'>
  <li >Total Cooking Time: {{hoverRecipe.totalTime}} min</li>
  <button v-on:click="handleClick" type="button" name="button">Details</button>
</ul>
</template>

<script>
import { eventBus } from '../main.js';
export default {
  name: 'recipe-item-cooking-time',
  props: ['hoverRecipe'],
  methods: {
    'handleClick': function(){
      eventBus.$emit('recipe-details', this.hoverRecipe)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
