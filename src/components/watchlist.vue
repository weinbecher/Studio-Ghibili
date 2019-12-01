<template lang="html">
<div class="">
  <ul>
    <h3 v-if = "watchlist">WatchList</h3>
    <!-- why is this not working? -->
    <li v-for="(film, index) in watchlist"  :film="film" :key="index">
      <p v-on:click="handleClick">
        {{ film.title }}
      </p>
    </li>
  </ul>
</div>

</template>

<script>
import { eventBus } from '../main.js'
export default {
  name:"watchlist",
  props:["watchlist"],
  methods: {
    handleClick(){
      eventBus.$emit('film-selected', this.film);
    }
    //not working
  }
}
</script>

<style lang="css" scoped>
</style>
