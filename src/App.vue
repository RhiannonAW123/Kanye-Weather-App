<template>
<div id='app'>

    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link href="https://fonts.googleapis.com/css2?family=Amatic+SC:wght@700&family=Rock+Salt&display=swap" rel="stylesheet">
     <kanye-quote class='k-quote' :quote="KanyeQuote"></kanye-quote>
     <weather-app></weather-app>
     <hr></hr>
     <h2>Weather App</h2>
</div>
  
</template>

<script>
import { eventBus } from './main.js'
import KanyeQuote from './components/KanyeQuote.vue'
import Weather from './components/Weather.vue'
export default {
  name: 'app',
  data(){
   return{
   KanyeQuote: undefined,
   city: undefined
   }
  },

  mounted() {
    fetch('https://api.kanye.rest/')
    .then(res => res.json())
    .then(KanyeQuote => this.KanyeQuote = KanyeQuote.quote)


  }, 
  components: {
    "kanye-quote": KanyeQuote,
    "weather-app": Weather
  }

}
</script>

<style lang='css' scoped>
#app {
  text-align: center;
  font-family: 'Amatic SC', cursive;
  background: rgb(248, 192, 239);
  color: black;
}
.k-quote {
  padding: 20px;
}
</style>