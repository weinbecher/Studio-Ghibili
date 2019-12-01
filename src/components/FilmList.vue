<template lang="html">
<div>
<film-list-item v-for="(film,index) in films" :film = "film" :key = "index"></film-list-item>
</div>
</template>

<script>
import FilmListItem from "@/components/FilmListItem";
export default {
  name:'film-list',
  pros:["films"],
  components:{
  "film-list-item":FilmListItem
  }
}

</script>

<style lang="css" scoped>
</style>
