<template>
  <div id="app" data-aos="fade">
    <div class="container-fluid">
      <div class="row">
        <div class="col">
        <h1 class="text-center mt-1 font-weight-bold">SPACE PROGRAM</h1>
        </div>
      </div>
      <div class="row ">
      <div class="col  mt-1">
        <h3   class="mt-3 m15 text-center ">WHAT'S HAPPENING?</h3>
        <app-space-news :newsArray="newsArray"></app-space-news>
      </div>
      <div class="col mx-5 mt-1">
        <div class="row">
          <div class="col mt-3">
            <h3 class="text-center">WHERE IS THE ISS?</h3>
            <app-map :markers='markers' :issLocation='issLocation'></app-map>
            
          </div>
        </div>
        <h3 class="text-center mt-4">FUN FACTS</h3>
        <div class="row centering">
          <div class="col-4 blocky" >
            <app-astronaut-list class="mb-5 "></app-astronaut-list>
          </div>
                    <div class="col">
                      
            <app-daily-image></app-daily-image>
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
import AstronautList from './components/AstronautList.vue'
import DailyImage from'./components/DailyImage.vue'
import DailyImageVue from './components/DailyImage.vue';
export default {
  data(){
    return{
      newsArray:[],
      issLocation:{},
      markers:[{position:{lat:0,lng:0}}]  
    }
  },
  components:{
    "app-space-news":SpaceNews,
    "app-map":ISSMap,
    "app-astronaut-list":AstronautList,
    "app-daily-image":DailyImageVue
  },
  created:function(){
    axios
      .get('https://newsapi.org/v2/top-headlines?q=space&country=us&category=science&apiKey=1b126c912d4843019ae079dd873530c0')
      .then(response => {
        this.newsArray = response.data.articles;
      })

  }
  
}
</script>

<style>
body{
  font-family: 'Quicksand', sans-serif;
}
.border {
    border-width:2px !important;
    
}
h1,h3{
  color: #8EB3FF;
}
h1{
  font-size: 65px
}
h3{
  font-size: 45px;
}
.bkg{
  background-color: #F8F9FD;
}
.m15{
  margin-left: 22px;
}
.centering{
  text-align: center
}
.blocky{
  display:inline-block
}

</style>
