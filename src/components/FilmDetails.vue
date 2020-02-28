<template lang="html">
<div v-if="film">
  <h1>{{film.title}}</h1>
  <h2>{{film.director}}</h2>
  <h3>{{film.release_date}}</h3>
  <p>{{film.description}}</p>
</div>
</template>

<script>
export default {
  name: 'film-detail',
  props: ['film']
}
</script>

<style lang="css" scoped>
</style>
