<template lang="html">
  <div class = "filmdetail" v-if="film">
  <h3>{{ film.title }}</h3>

  <p>Description: {{film.description}}</p>

  <p>Release Date: {{film.release_date}}</p>


  <!-- <p>people: {{film.people}}</p> -->
  </div>

</template>

<script>
export default {
  name: 'film-detail',
  props:['film']
}
</script>

<style lang="css" scoped>
.filmdetail {
  width: 60%;
  justify-content: space-between;

}
</style>
