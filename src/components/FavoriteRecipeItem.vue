<template lang="html">
<li>{{recipe.recipe.label}}</li>
<!-- add a made and then differculty input item -->
</template>

<script>
export default {
  name: 'favorite-recipe-item',
  props: ['recipe']
}
</script>

<style lang="css" scoped>
</style>
