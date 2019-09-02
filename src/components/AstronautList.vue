<template>
  <div>
      <h4 style="color:#8EB3FF">WHO'S IN SPACE</h4>
      <ul class="list-group ">
          <a href="" class="list-group-item list-group-item-action" v-for="(astronaut,index) in astronautArray" :key="index">{{astronaut.name}}</a>
      </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
data:function(){
    return{
        astronautArray:[]
    }
},
methods:{},
created:function(){
    axios
        .get("http://api.open-notify.org/astros.json")
        .then(response=>{
            this.astronautArray = response.data.people;
        })
}
}
</script>

<style scoped>
.list-group{
      display:inline-block;
 }
 
</style>