<template>
  <div id="app">
      <h2>Studio Ghibi Films</h2>
    <div class="main-container">
      <film-list :films='films'></film-list>
      <film-detail :film='selectedFilm'></film-detail>
      <watchlist :watchList = "watchlist"></watchlist>
       <!-- why is this not working -->
   </div>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import FilmList from './components/FilmList.vue';
import FilmDetail from './components/FilmDetail.vue'
import WatchList from './components/WatchList.vue'

export default {
  name: 'app',
  data(){
    return {
      films: [],
      selectedFilm: null
    };
  },
  computed: {
  watchList: function() {
    return this.films.filter(film => film.addWatchList);
  }
},
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    // .then(films => this.films = films)

    .then(films => {
        films.forEach(film => (film.addWatchList = false));
        //don't understand, isFavourite?
        this.films = films;
      })

    eventBus.$on('film-selected',(film)=>{
      this.selectedFilm = film;}),

    eventBus.$on("watchlist-added",(film) =>{
       this.addToWatchList(film)})
    },

  components: {
    "film-list": FilmList,
    "filmDetail": FilmDetail,
    "watchlist": WatchList
  },

  methods:{
    addToWatchList: function(film){
      const index = this.films.indexOf(film);
      this.films[index].addWatchList = true;

    }
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
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
