<template>
  <div>
    <h1 class="display-1 text-center">Weather App</h1>
      <v-flex xs12>

          <v-card color="blue">

              <v-card-text>
                  <v-layout>
                  <v-flex v-if="weather.main" class="text-center">
                      <h4>Temperature</h4>
                     <h1 class="display-1"> {{weather.name}} </h1>
                     <img :src="icon">
                     <p>
                         <span class="display-1"> {{ temp() }} &#176;C </span>
                     </p>

                   

                  </v-flex>
                  </v-layout>
              </v-card-text>

          </v-card>

      </v-flex>

        <v-form @submit.prevent="getWeatherInfo">
      <v-flex xs12 class="mt-4">
          <v-text-field 
            label="Enter City Name"
            outlined
            v-model="city"
          ></v-text-field>
      </v-flex>
        </v-form>


  </div>
</template>

<script>
export default {
layout:'weatherlayout',

data()
{
    return {
        city:"London",
        weather:{}
    }
},
created() 
{
    this.getWeatherInfo()
},

computed:{

    icon(){
        return this.weather.weather
        ? `https://openweathermap.org/img/wn/${this.weather.weather[0].icon}.png`
        : ''
    }
},

asyncData({params,$axios})
{
    return $axios

    .$get( `https://api.openweathermap.org/data/2.5/weather?q=London&appid=858c9973ec65468309c3541d8c8d36f3`

    )
    .then(res=>{
        return{weather:res}
    })
},



methods:
{
    getWeatherInfo()
    {
            this.$axios
    .get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=858c9973ec65468309c3541d8c8d36f3`
)
    .then(res=>(this.weather=res.data))
    },

    temp()
    {
        return this.weather.main ? Math.round(this.weather.main.temp - 273): ''
    }


}





}
</script>

<style>


</style>