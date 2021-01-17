<template>
  <div class='weather-section'>
      <h1 class='weather-title'>Weather App</h1>
          <label class='pick-a-city' for='city'>Choose a city</label>
          <br>
          <input type='text' id='city' name='city' v-model='cityInput' value=''>
          <br>
          <button class='weather-button' v-on:click='getWeather(cityInput)'>Get Weather Info</button>
          <br>
          <p v-if='infoFromAPI'>Place - {{ infoFromAPI.name }}</p>
          <p v-if='infoFromAPI'>{{ infoFromAPI.weather[0].description }}</p>
          <p v-if='infoFromAPI'>Temp ... {{ infoFromAPI.main.temp }} C°</p>
          <p v-if='infoFromAPI'>Wind Speed - {{ infoFromAPI.wind.speed }}</p>
          <img id="icon" v-if="iconurl" v-bind:src="iconurl" alt="Weather icon">


  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'weather-app',
  data () {
      return {
          cityInput: undefined,
          infoFromAPI: null,
          weatherIcon: null,
          iconurl: null

      }
  },
  props: ['city'],
  methods: {
     async getWeather(cityInput) {
        const key = 'f70c633e90e1f06b2571a612affd27fe';
        await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${cityInput}&appid=${key}&units=metric`)
        .then(res => res.json())
        .then(city => this.infoFromAPI = city);


        this.weatherIcon = this.infoFromAPI.weather[0].icon;
        this.iconurl = `http://openweathermap.org/img/w/${this.weatherIcon}.png`;


    },

    }
}

</script>

<style lang='css' scoped>
.weather-title {
    padding: 15px;
    background-color: black;
    color: rgb(252, 228, 248);
}

.weather-button { 
   padding: 20px; 
   border-radius: 6px;
   font-family: 'Amatic SC', cursive;
   font-size: 20px;
   background-color: rgb(0, 0, 0); 
   color: rgb(252, 228, 248);
}

.pick-a-city { 
   padding: 10px; 
   font-family: 'Amatic SC', cursive;
   font-size: 20px;
   background-color: rgb(0, 0, 0); 
   color: rgb(252, 228, 248);    
}

</style>