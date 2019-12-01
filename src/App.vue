<template>
  <div id="app">
    <h2>Film List of Studo Ghibili</h2>
    <film-list :films = "films"></film-list>
  </div>
</template>

<script>
import FilmList from '@/components/FilmList.vue'

export default {
  name: 'app',
  components: {
    "film-list":FilmList
  },
  data(){
    return{
      films:[],
      selectedFilm: null
    }
  },
  methods:{
    getFilms: function(){
      fetch("https://ghibliapi.herokuapp.com/films")
      .then(res => res.json())
      .then(data => this.films = data  )
    }
  },
  mounted(){
    this.getFilms();
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
