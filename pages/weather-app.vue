<template>
    <v-container>
<!--      <v-layout>-->
      <h1 class="display-1 text-center" style="margin-bottom: 20px">Weather App</h1>
        <v-flex xs12 class="display-1 text-center">
          <v-card color="blue-gray darken-2" dark>
            <v-card-text>
              <v-layout v-if="weather.weather" justify-center>

<!--                //Temp-->
                <v-flex class="text-center" v-if="weather.main">
                  <h4>Temperature</h4>
                  <h1 class="display-1" style="color:#f5ff00 ">{{weather.name}}</h1>
                  <img :src="icon" alt="weather icon">
                  <p><span style="color: darkorange" class="display-1">{{temp()}} &#176;C</span></p>
                  <p><span class="caption ml-4">{{weather.weather[0].description}}</span></p>
                </v-flex>

<!--                //Pres & Wind-->
                <v-flex class="text-center" v-if="weather.main">
                  <h4>Wind And Pressure</h4>
                  <h1 class="headline mt-4" style="color:#f5ff00 ">
                    Wind: {{weather.wind.speed}} m/s {{weather.wind.deg}} &deg;
                  </h1>
                  <h1 class="headline mt-4" style="color:#00ccff ">
                    Humidity: {{weather.main.humidity}} %
                  </h1>
                  <h1 class="headline mt-4" style="color:#00ff8e ">
                    Pressure: {{weather.main.pressure}} hPa
                  </h1>
                </v-flex>

                <v-flex class="text-center" v-if="weather.main">
                  <h4>Other</h4>
                  <h1 class="headline mt-4" style="color:#00ccff ">
                    Max Temperature: {{Math.round(weather.main.temp_max -273)}} &deg; C
                  </h1>
                  <h1 class="headline mt-4" style="color:#00ccff ">
                    Min Temperature: {{Math.round(weather.main.temp_min -273)}} &deg; C
                  </h1>
                </v-flex>

              </v-layout>
            </v-card-text>
          </v-card>
        </v-flex>

<!--      //TODO: enter after write city in field to go request-->
      <form>
        <v-flex xs12 class="mt-4">
          <v-text-field solo label="Enter City Name" v-model="city"></v-text-field>
        </v-flex>
      </form>

      <div>
<!--        //TODO:May call this computed in updated hooks function-->
<!--        {{getWeatherInfo}}-->
<!--        Todo:If you want to display data direct before created hook function load should-->
<!--         be use asyncData function and move to SSR-->
        {{weather.weather[0]}}<br>
        {{weather.main}}
      </div>
<!--      </v-layout>-->
    </v-container>
</template>

<script>
  export default {
    name : 'weather-app',
    data(){
      return{
        weatherAppId:'913917a63abeb8f987f2a74faa0615c8',
        city:'London',
        weather:{}
      }
    },
    //TODO:To initialize data before render it by move to (SSR)
    //TODO:Cannot use in it any variables because does not load before
    asyncData ({$axios}) {
      return $axios.$get(
        'https://api.openweathermap.org/data/2.5/weather?q=' +
        'London'+
        '&appid=913917a63abeb8f987f2a74faa0615c8'
      ).then(res=>{
        return {
          weather:res
        }
      })
    },
    created () {
      this.getWeatherInfo
    },
    computed:{
      icon(){
        return this.weather.weather
          ? 'https://openweathermap.org/img/wn/'+this.weather.weather[0].icon+'.png':''
      },
      getWeatherInfo(){
        this.$axios.$get(
          'https://api.openweathermap.org/data/2.5/weather?q=' +
          this.city+
          '&appid='+this.weatherAppId
        ).then(res=>{
          console.log(res)
          this.weather=res
        })
      },
    },
    methods:{
      temp(){
        return this.weather.main ? Math.round(this.weather.main.temp -273) :''
      }
    },
    updated(){
      this.getWeatherInfo
    }
  }
</script>

<style scoped>

</style>
