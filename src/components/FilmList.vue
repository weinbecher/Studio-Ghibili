<template lang="html">
  <div class="filmlist">
    <ul>
      <film-list-item v-for="(film, index) in films" :film="film" :key="index"></film-list-item>
    </ul>
  </div>

</template>

<script>
import FilmListItem from './FilmListItem.vue';

export default {
  name: 'film-list',
  props: ['films'],
  components: {
    "film-list-item": FilmListItem
  }
}
</script>

<style lang="css" scoped>
.filmlist {
  width: 60%;
  overflow-y: scroll;
  display: flex;
  flex-wrap: wrap;
}
</style>
