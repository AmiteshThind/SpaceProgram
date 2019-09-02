<template>
<div>
<h4 style="color:#8EB3FF">IMG OF THE DAY</h4>
<div class="card" style="width: 100%;">
  <img class="card-img-top" style="height: 10rem;" :src="imageOftheDay.url" alt="Card image cap">
  <div class="card-body ">
    <p class="card-text scrolling" style="font-size:15px; height:5.5rem">{{imageOftheDay.explanation}}</p>
  </div>
</div>
</div>
</template>

<script>
import axios from 'axios'
export default {
    data:function(){
        return{
            imageOftheDay:{}
        }
    },
created:function(){
    axios
    .get('https://api.nasa.gov/planetary/apod?api_key=yL6a4rALDpVsKpXUOEOjFINyPezjyIhi60gKa9LG')
    .then(response=>{
        this.imageOftheDay=response.data;
    })
}

}
</script>

<style scoped>
.scrolling{
    float:left;
overflow-y: auto;
height: 768px;

}
 

 
html {
  overflow: -moz-scrollbars-vertical; 
    overflow-y: scroll;
}
p{
    color: #494D52
}

::-webkit-scrollbar {

width: 7px; /* remove scrollbar space /
background: transparent; / optional: just make scrollbar invisible /

/ optional: show position indicator in red */
}
::-webkit-scrollbar-thumb {
    border-radius: 5px;
background: #8EB3FF
}



</style>