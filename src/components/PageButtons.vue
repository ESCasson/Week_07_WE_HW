<template lang="html">
  <div class="">
    <button type="button" name="button" v-on:click='pageForward'>Forward 12</button>
    <button type="button" name="button" v-on:click='pageBackward'>Backwards 12</button>

  </div>
</template>

<script>
import { eventBus } from '../main.js';
export default {
  name: "page-buttons",
  props: ['pageFrom', 'pageTo'],
  methods: {
    pageForward: function(){
      this.pageTo = this.pageTo + 12,
      this.pageFrom =this.pageFrom + 12,
      eventBus.$emit('page-to', this.pageTo),
      eventBus.$emit('page-from', this.pageFrom)
    },

    pageBackward: function(){
      if (this.pageFrom > 0) {
      this.pageTo = this.pageTo - 12,
      this.pageFrom =this.pageFrom - 12,
      eventBus.$emit('page-to', this.pageTo),
      eventBus.$emit('page-from', this.pageFrom)
    }
    }
  }
}
</script>

<style lang="css" scoped>
</style>
