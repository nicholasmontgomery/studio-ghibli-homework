<template lang="html">
  <div>
    <ul>
      <list-item v-for="film in films" :film="film"/>
    </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue'

export default {
  name: 'films-list',
  props: ['films'],
  components: {
    "list-item": ListItem
  }
}
</script>

<style lang="css" scoped>
</style>
