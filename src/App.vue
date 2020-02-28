<template lang="html">
  <h1>Ghilbi Film Studio</h1>

</template>

<script>
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
  }
}
</script>

<style lang="css" scoped>
</style>
