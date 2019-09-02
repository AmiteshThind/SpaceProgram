<template>
  <GmapMap
  :center="{lat:Number(issLocation.latitude), lng:Number(issLocation.longitude)}"
  :zoom="3"
  map-type-id="satellite"
  style="width: 500px; height: 300px"
  id="map"
>
  <GmapMarker
    :key="index"
    v-for="(m, index) in markers"
    :position="m.position"
    :clickable="true"
  />
</GmapMap>
</template>

<script>

export default {
  props:['issLocation'],
    data(){
        return{
            markers:[{position:{lat:Number(this.issLocation.latitude),lng:Number(this.issLocation.longitude)}}]     
            
        }
    }

  

}
</script>

<style>

</style>