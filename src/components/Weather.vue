<template>
  <div>

  <h2>Weather</h2>
  <!-- <h1>{{ weather.name }}</h1> -->
  <!-- <img :src="'http://openweathermap.org/img/w/' + weather.weather[0].icon  + '.png'">  -->
  <ul v-if="weather">

    <li>
      Current temp: {{ weather.main.temp }}&deg;C
    </li>
    <li>
      Min: {{ weather.main.temp_min }}&deg;C | Max: {{ weather.main.temp_max }}&deg;C
    </li>
    <li>
      Wind speed: {{ weather.wind.speed }}km/h
    </li>
    <li>
      Sunrise: {{ weather.sys.sunrise | moment("h:mm") }} a.m. | Sunset: {{ weather.sys.sunset | moment("h:mm") }} p.m.
    </li>
  </ul>

</div>

</template>


<script>
/* eslint-disable */

import axios from 'axios'

export default {
  name: 'weather',
  data () {
    return {
      weather: ''
    }
  },
  mounted () {
  axios
    .get('//api.openweathermap.org/data/2.5/weather?lat=-33.885202&lon=151.137126&units=metric&appid=f57b5dc360602d94c11101819f5428ab')
    .then(response => (this.weather = response.data ))
  }
}
</script>
