<template>
   <div class="view"> 
    <div class="left"><button>left</button></div>
    <div class="widget">
        <component v-bind:is="component"></component>
    </div>
    <div class="right"><button @click="right">right</button></div>
    </div>
</template>

<script>
import weather from '../components/weather.vue'
import finance from '../components/stocks.vue'

export default {
  components: {
    finance: finance,
    weather: weather,
    
  },
  data() {
    return{
      component: 'finance'
    }
  },
  methods: {
    right(e){
      this.component = weather;
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
