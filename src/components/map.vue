<template lang="html">
  <head>
     <div id="mapid"></div>
  </head>

</template>

<script>
import L from 'leaflet';
import { LMap, LTileLayer, LMarker } from 'vue2-leaflet';

export default {
    name: 'map',
    components: {
      LMap,
      LTileLayer,
      LMarker,
    },
  };
</script>

<style lang="css" scoped>
  #mapid { height: 180px; }
</style>
