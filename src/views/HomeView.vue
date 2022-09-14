<template>
   <div class="view"> 
    <div class="left"><button @click="left">left</button></div>
    <div class="widget">
        <component v-bind:is="component"></component>
    </div>
    <div class="right"><button @click="right">right</button></div>
    </div>
</template>

<script>
import weather from '../components/weather.vue'
import finance from '../components/stocks.vue'
import news from '../components/news.vue'

export default {
  components: {
    finance: finance,
    weather: weather,
    news: news
    
  },
  data() {
    return{
      component: 'finance'
    }
  },
  methods: {
    right(e){
      console.log(this.component)
      if(this.component == 'finance'){
      this.component = news;
      console.log("druga")
      }else if(this.component == 'news'){
        console.log("geška")
        this.component = finance;
      }
    },
    left(e){
      this.component = news;
    }
  }
}
</script>

<style scoped>
.view{
  display: flex;
  justify-content: space-between;
  width:100vw;

}
.widget{
  display: flex;
  align-items: center;
  justify-content: center;
}

.left{
  width: 20vw;
}
.right{
  width: 20vw;
    
}
</style>
