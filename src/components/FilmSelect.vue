<template lang="html">
  <div>
    <h1>Pick a film</h1>
    <select @change="handleClick" v-model="selectedFilm">
      <option v-for='film in films' :value='film'>{{film.title}}</option>
    </select>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'film-select',
  data() {
    return {
    selectedFilm: {}
  }
},
  props: ['films'],
  methods: {
    handleClick(){
      eventBus.$emit('film-selected', this.selectedFilm)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
