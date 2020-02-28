<template lang="html">
  <div class="">
    <h1>Ghilbi Film Studio</h1>
    <div class="main container">
      <film-select :films='films'/>
      <film-detail :film='selectedFilm'/>
    </div>
  </div>


</template>

<script>
import FilmSelect from './components/FilmSelect.vue'
import FilmDetail from './components/FilmDetails.vue'
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
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(result => result.json())
    .then(films => this.films = films)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film;
    })
  },
  components: {
    "film-select": FilmSelect,
    "film-detail": FilmDetail
  }
}
</script>

<style lang="css" scoped>
</style>
