<template>
  <div>
      <h1>Weather Stuff</h1>
          <label for='city'>Choose a city</label>
          <input type='text' id='city' name='city' v-model='cityInput' value=''>
          <button v-on:click='getWeather(cityInput)'>Get Weather Info</button>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'weather-app',
  data () {
      return {
          cityInput: undefined,
          infoFromAPI: null
      }
  },
  props: ['city'],
  methods: {
     getWeather(cityInput) {
        const key = 'f70c633e90e1f06b2571a612affd27fe';
        fetch(`https://api.openweathermap.org/data/2.5/weather?q=${cityInput}&appid=${key}&units=metric`)
        .then(res => res.json())
        .then(city => this.infoFromAPI = city)
  }
}
}
</script>

<style>

</style>