<template lang="html">
  <div>
    <h1>Pick a film</h1>
    <input type="text" v-model="search" placeholder="search-films">
    <ul>
      <list-item v-for="film in filteredFilms" :film="film"/>
    </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue'

export default {
  name: 'films-list',
  props: ['films'],
  data() {
    return {
    search: ""
  }
},
  components: {
    "list-item": ListItem,
  },
  computed: {
    filteredFilms: function() {
      return this.films.filter((film) => {
        return film.title.toLowerCase().match(this.search.toLowerCase());
      });
    }
  },
}
</script>

<style lang="css" scoped>
</style>
