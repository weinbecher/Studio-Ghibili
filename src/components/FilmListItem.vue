<template lang="html">
  <div class="filmlistitem">
    <li v-on:click = "handleClick">{{film.title}}
      <button v-on:click="handleClick"> ...</button>
      <button v-on:click="addWatchList"> + </button>

</li>

  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'list-item',
  props: ['film'],
  methods: {
    handleClick(){
      eventBus.$emit('film-selected', this.film);
    },

    addWatchList(){
      eventBus.$emit("watchlist-added", this.film);
    }
  }
}
</script>

<style lang="css" scoped>

.filmlistitem {
  display: flex;
  flex-direction: column;
  list-style-type: none;
  padding: 10px;
}

button {
  font: bold 20px ;
  text-decoration: none;
}


</style>
