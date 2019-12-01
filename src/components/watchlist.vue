<template lang="html">
<div class="">
  <h2>WatchList</h2>
  <ul>
    <li v-for="(film, index) in watchlist"  :film="film" :key="index">
      <p v-on:click="handleClick">
        {{ film.title }}
      </p>
    </li>
  </ul>
</div>

</template>

<script>
export default {
  name:"watchlist",
  props:["watchlist"],
  methods: {
    handleClick(){
      eventBus.$emit('film-selected', this.film);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
