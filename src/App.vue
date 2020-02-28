<template lang="html">
  <div class="">
    <h1>Ghilbi Film Studio</h1>
    <div class="main container">
      <films-list :films='films'/>
      <list-item :film='film'/>
      <film-detail :film='selectedFilm'/>
    </div>
  </div>


</template>

<script>
// import FilmSelect from './components/FilmSelect.vue'
import FilmDetail from './components/FilmDetails.vue'
import ListItem from './components/ListItem.vue'
import FilmsList from './components/FilmsList.vue'
import {eventBus} from './main.js'

export default {
  name: 'App',
  data(){
    return {
      films: [],
      selectedFilm: {}
    };
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films/')
    .then(result => result.json())
    .then(films => this.films = films)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film;
    })
  },
  components: {
    "films-list": FilmsList,
    "list-item": ListItem,
    "film-detail": FilmDetail
  }
}
</script>

<style lang="css" scoped>
</style>
