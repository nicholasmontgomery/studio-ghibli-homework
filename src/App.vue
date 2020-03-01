<template lang="html">

  <div class="">
    <img src="../public/studio-ghibli-title.svg" alt="ghibli-title" id="ghibli-title">
    <h1>Ghilbi Film Studio</h1>
    <div class="main container">
      <films-list :films='films'/>
      <list-item :film='film'/>
      <film-detail :film='selectedFilm'/>
    </div>
    <div id="map">
      <l-map
      v-if="showMap"
      :zoom="zoom"
      :center="center"
      :options="mapOptions"
      style="height: 80%"
      >
      <l-tile-layer
      :url="url"
      :attribution="attribution"
      />
      </l-map>
    </div>
  </div>

</template>

<script>
import FilmDetail from './components/FilmDetails.vue'
import ListItem from './components/ListItem.vue'
import FilmsList from './components/FilmsList.vue'
import {eventBus} from './main.js'
import { latLng } from "leaflet";
import { LMap, LTileLayer, LMarker } from 'vue2-leaflet';


export default {
  name: 'App',
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
    "film-detail": FilmDetail,
    LMap,
    LTileLayer,
    LMarker
  },
  data(){
    return {
      films: [],
      selectedFilm: {},
      zoom: 13,
      center: latLng(35.7019, 139.5241),
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution:
      '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      currentZoom: 11.5,
      center: latLng(35.7019, 139.5241),
      showParagraph: false,
      mapOptions: {
        zoomSnap: 0.5
      },
      showMap: true
    }
  }
}
</script>

<style lang="css" scoped>

h1 {
  font-family: "ヒラギノ角ゴ Pro W3";
}

#yeah-baby{
  height: 300px;
}

#map {
  height: 500px;
  width: 75%
}

#ghibli-title {
  height: 500px;
  width: 75%
}
</style>
