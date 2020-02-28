<template>
    <div class="row map">
        <h2>Center is {{currentCenter}}, zoom is {{currentZoom}}</h2>
        <l-map @update:zoom="zoomUpdate" @update:center="centerUpdate"
            :zoom="zoom" :center="center">
        <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
        <l-marker :key="index" v-for="(brew,index) in brews"
                :lat-lng="latLng(brew.latitude,brew.longitude)"
                >
            <l-icon :icon-size="iconSize" :icon-url="icon"></l-icon>    
            <l-popup>{{brew.name}},{{brew.city}},{{brew.state}}</l-popup>
        </l-marker>
    </l-map>
    </div>
</template>
<script>
import { LMap, LTileLayer, LMarker,LPopup,LIcon } from 'vue2-leaflet';
import beer from '../assets/beer.png'
export default {
    components:{LMap,LTileLayer, LMarker,LPopup, LIcon},
     props:{brews:Array},
    data() {
    return {
      zoom:6, currentZoom:6,
      center: L.latLng(32.2467372722906, -110.992750525872),
      currentCenter:L.latLng(32.2467372722906, -110.992750525872),
      url:'https://tile.thunderforest.com/cycle/{z}/{x}/{y}.png?apikey=a1f6329b5a3f46dd9a41e5eb76d551e8',
      attribution:'&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      marker: L.latLng(47.413220, -1.219482),
      icon:beer,
      iconSize:[50,50]
    }
  },
  methods:{   latLng(lat,lng){ return L.latLng(lat,lng)    } ,
              centerUpdate(c){return this.currentCenter=c;},
              zoomUpdate(c){return this.currentZoom=c;}  
          }
   
}
</script>
<style lang="scss" scoped>
 .map{ height:90vh}
</style>
