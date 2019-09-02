<template>

   <div class="card" style="width:15rem" >
     <a :href="newsData.url" class="ho">
      <img class="card-img-top" :src="newsData.urlToImage" alt="Card image cap" style="height:10rem;padding:2px">     
      <div class="card-body">
      <h5 class="card-title" >{{newsData.title}}</h5>
   </div>
    </a>
</div>
</template>
<script>
export default {
    props:['newsData'],
    created:function(){
    
        if(this.newsData.urlToImage==null){
          this.newsData.urlToImage="https://cdn.spacetelescope.org/archives/images/thumb700x/potw1931a.jpg";
        }
        

      
        
      }
    }

    

</script>
<style scoped>
.card{
  margin-left: 10px;
  margin-right: 10px;
  margin-top: 15px;
  margin-bottom: 10px;
  transition: transform .2s;
}
a{
    text-decoration: none;
  color: #494D52
}
.card-title{
  font-size: 15px;
  
  
}
.ho:hover{
   color: #FFFF;
  
}
.card:hover{
   transform: scale(1.1);
   background-color:#8EB3FF;
}

.card-text{
  font-size: 13px;
 font-family: 'Open Sans', sans-serif;
 
}


</style>
