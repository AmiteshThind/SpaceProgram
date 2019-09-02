<template>
  <GmapMap
  class="border"
   :center="{lat:Number(this.issLocation.latitude), lng:Number(this.issLocation.longitude)}"
    :zoom="3"
    map-type-id="satellite"
    style="width: 100%; height: 25rem"
    id="map">
    <GmapMarker  :icon="markers[0].icon" :position="markers[0].position" :clickable="true"/>
  </GmapMap>
</template>

<script>
import axios from 'axios'
export default {

    data(){
        return{
            issLocation:{
              latitude:0,longitude:0
            }               
        }
    },
    computed:{
       markers(){
         return [{
           position:{lat:Number(this.issLocation.latitude),lng:Number(this.issLocation.longitude),
           icon:'https://p7.hiclipart.com/preview/479/176/868/nasa-insignia-budget-of-nasa-international-space-station-logo-nasa.jpg'
           }}]
      }
    },
    methods:{
    issLocationCall:function(){
      axios
        .get('http://api.open-notify.org/iss-now.json')
        .then(response => {
        this.issLocation=response.data.iss_position;
        console.log(this.issLocation)
        })
      },
    intervalFetchData: function () {
            setInterval(() => {    
                this.issLocationCall();
                }, 1000);    
                console.log(this.issLocation)
        }
    },
    mounted:function(){
      this.issLocationCall();
      this.intervalFetchData();
    }
}
  

</script>

<style>
.border{
  border-radius: 5px;
}

</style>