<template>
  <div>
    <div class="text-center font-bold">Select From Map:</div>
    <div id="map"></div>
  </div>
</template>

<script>
import mapboxgl from 'mapbox-gl/dist/mapbox-gl.js'
import MapboxGeocoder from '@mapbox/mapbox-gl-geocoder';
import '@mapbox/mapbox-gl-geocoder/dist/mapbox-gl-geocoder.css';
export default {
  name: "Map",
  components: {

  },
  data(){
    return{
    }
  },
  emits:['sendCoord'],
  methods:{
    getCity(){
      console.log('cityyyyyyyyyy')
    },

  },
  mounted() {
    mapboxgl.accessToken = 'pk.eyJ1IjoicGFyYXN0d28iLCJhIjoiY2t4dDhpZjQ0MXRnejJub2VoY3JscjNrcCJ9.2FJvxaabbIL2UwT3f0rdSQ';
    // eslint-disable-next-line no-unused-vars
    var map = new mapboxgl.Map({
      container: 'map',
      style: 'mapbox://styles/mapbox/streets-v11'
    });
    let geoCoder = new MapboxGeocoder({
      accessToken: mapboxgl.accessToken,
      mapboxgl: mapboxgl,
    });
    map.addControl(
        geoCoder
    );
    // const marker = new mapboxgl.Marker({
    //   draggable: true
    // })
    //     .setLngLat([0, 0])
    //     .addTo(map);
    geoCoder.on('result', (e)=>{
      this.$emit('sendCoord', e.result.center);
    });
  },


}
</script>

<style scoped>
@import '../assets/styles/mapbox.css';
#map{
  width: 336px;
  height: 300px;
}
</style>