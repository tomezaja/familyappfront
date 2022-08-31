<template>
  <div class="weather">
    <div class="search-box">
        <input type="text" v-model="query" @keypress="findWeather"/>
    <div class="w-location">
        {{weather.name}}, {{ weather.sys.country }}
      
    </div>
        <div class="w-weather">
            
            <div class="temp">{{ Math.round(weather.main.temp) }}°c</div>
            <div class="description"> {{ weather.weather[0].main }}</div>
            <div class="feels">Feels like: {{ Math.round(weather.main.feels_like) }}°c</div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    data () {
        return{
            api_key: '5eeaa4bc375546132ba9c67b62749260',
            query: '',
            weather: {}
        }
    },
    methods: {
        defaultWeather(){
            fetch(`https://api.openweathermap.org/data/2.5/weather?q=zagreb&units=metric&appid=${this.api_key}`)
                    .then(res => {
                        return res.json();
                    }).then(this.setResult);
            
            },
        findWeather(e){
            if(e.key == "Enter"){
                fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.query}&units=metric&appid=${this.api_key}`)
                    .then(res => {
                        return res.json();
                    }).then(this.setResult);
            }
        },
        setResult(result){
            this.weather = result;
        }
    },
    
    beforeMount(){
    	this.defaultWeather()
    }
    
}
</script>

<style lang="scss" scoped>

input{
    background-color: aliceblue;
}
.w-location {
  color: var(--fresh);
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  
}
.w-weather {
  text-align: center;
  font-style: italic;
}
.w-weather .description{
    color: var(--light)
    
}
.w-weather .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #FFF;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color:rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0px;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
.w-weather .weather {
  color: #FFF;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
</style>