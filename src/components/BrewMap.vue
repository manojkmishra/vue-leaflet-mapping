<template>
    <div class="row map">
         <l-map :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <l-marker :key="index" v-for="(brew,index) in brews"
                :lat-lng="latLng(brew.latitude,brew.longitude)"
                >
      </l-marker>
    </l-map>
    </div>
</template>
<script>
import { LMap, LTileLayer, LMarker } from 'vue2-leaflet';

export default {
    components:{LMap,LTileLayer, LMarker},
     props:{brews:Array},
    data() {
    return {
      zoom:13,
      center: L.latLng(47.413220, -1.219482),
      url:'https://tile.thunderforest.com/cycle/{z}/{x}/{y}.png?apikey=a1f6329b5a3f46dd9a41e5eb76d551e8',
      attribution:'&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      marker: L.latLng(47.413220, -1.219482),
    }
  },
  methods:{   latLng(lat,lng){ return L.latLng(lat,lng)    }  }
   
}
</script>
<style lang="scss" scoped>
 .map{ height:90vh}
</style>
