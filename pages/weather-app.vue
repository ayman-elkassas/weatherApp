<template>
    <v-container>
<!--      <v-layout>-->
      <h1 class="display-1 text-xs-center">Weather App</h1>
        <v-flex xs12>
          <v-card color="blue-gray darken-2" dark>
            <v-card-text>
              <v-layout v-if="weather.weather" justify-center>
                <v-flex class="text-xs-center">
                  <h4>Temperature</h4>
                  <h1 class="display-1">{{weather.name}}</h1>
                  <img :src="weather.weather[0].icon" alt="weather icon">
                </v-flex>
              </v-layout>
            </v-card-text>
          </v-card>
        </v-flex>

<!--      //TODO: enter after write city in field to go request-->
      <form @submit.prevent="getWeatherInfo">
        <v-flex xs12 class="mt-4">
          <v-text-field solo label="Enter City Name" v-model="city"></v-text-field>
        </v-flex>
      </form>

      <div>
        {{this.weather}}
      </div>

<!--      </v-layout>-->
    </v-container>
</template>

<script>
  export default {
    name : 'weather-app',
    data(){
      return{
        city:'London',
        weather:{}
      }
    },
    created(){
      this.getWeatherInfo();
    },
    methods:{
      getWeatherInfo(){
        this.$axios.$get(
          'https://api.openweathermap.org/data/2.5/weather?q=' +
          this.city+
          '&appid=913917a63abeb8f987f2a74faa0615c8'
        ).then(res=>{
          console.log(res)
          this.weather=res
        })
      }
    }
  }
</script>

<style scoped>

</style>
