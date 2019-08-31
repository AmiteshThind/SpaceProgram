<template>
  <div id="app">
    <div class="container-fluid">
      <div class="row">
        <div class="col">
        <h1 class="text-center mt-3">How's Space?</h1>
        </div>
      </div>
      <div class="row ">
      <div class="col mx-5 mt-3 border rounded bkg ">
        <h3 class="mt-3 text-center">Space News</h3>
        <app-space-news :newsArray="newsArray"></app-space-news>
      </div>
      <div class="col mx-5 mt-3">
        <div class="row">
          <div class="col">
            <h3>ISS Location</h3>
            <app-map :issLocation='issLocation'></app-map>
            
          </div>
        </div>
        <div class="row">
          <div class="col">
            <h3>People In Space</h3>
          </div>
        </div>
      </div>
      </div>
    </div>
    
  </div>
</template>

<script>
import axios from 'axios';
import ISSMap from './components/ISSMap.vue'
import SpaceNews from "./components/SpaceNews.vue"
export default {
  data(){
    return{
      newsArray:[],
      issLocation:{}
    }
  },
  components:{
    "app-space-news":SpaceNews,
    "app-map":ISSMap
  },
  created:function(){
    axios.all([
      axios.get('https://newsapi.org/v2/top-headlines?q=space&country=us&category=science&apiKey=1b126c912d4843019ae079dd873530c0'),
      axios.get('http://api.open-notify.org/iss-now.json')
    ])
      .then(responseArr => {
        this.newsArray = responseArr[0].data.articles;
        this.issLocation=responseArr[1].data.iss_position;
      })
 
  }
  
}
</script>s

<style>
body{
  font-family: 'Baloo', cursive;
}
.border {
    border-width:5px !important;
    border-color: #8EB3FF !important;
}
h1,h3{
  color: #8EB3FF;
}
h1{
  font-size: 45px
}
.bkg{
  background-color: #F8F9FD;
}

</style>
