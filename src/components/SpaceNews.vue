<template>
 
    <div class="row scroll justify-content-center">
        <app-news-card v-for="(newsData,index) in newsArray" :key='index' :newsData="newsData"></app-news-card>
    </div>

</template>
<script>
import NewsCard from "./NewsCard.vue"
export default {
    data(){
        return{
                height:0
        }
    },
    props:['newsArray'],
    components:{
        "app-news-card":NewsCard
    },
    created:function(){
               let i;

      for(i=0;i<this.newsArray.length;i++){
        if(this.newsArray[i].description == null){
          
          this.newsArray.splice(i,1);
        }
      }

      var body = document.body,
    html = document.documentElement;

                    this.height = Math.max( body.scrollHeight, body.offsetHeight, 
                       html.clientHeight, html.scrollHeight, html.offsetHeight );
                       console.log(this.height)
    }
}
</script>
<style scoped>
body{
    overflow-y: auto;
}
.scroll{
    float:left;
overflow-y: auto;
height: 768px;

}
html {
  overflow:   scroll;
}
::-webkit-scrollbar {
    width: 0px;
    background: transparent; /* make scrollbar transparent */
}

</style>
