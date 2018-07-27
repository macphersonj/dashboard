<template>
  <div>

  <h2>Weather</h2>
  <!-- <h1>{{ weather.name }}</h1> -->
  <!-- <img :src="'http://openweathermap.org/img/w/' + weather.weather[0].icon  + '.png'">  -->

  <div v-if="weather" class="mt-10 max-w-sm rounded overflow-hidden shadow-lg bg-white p-6 text-grey">
    <div class="flex mb-4">
      <div class="w-1/2">
        <h2 class="text-3xl leading-none font-thin text-grey">{{ weather.name }}</h2>
        <div class="bg-grey w-1/2 rounded my-2" style="height: 3px;">
        </div>
        <div class="flex items-center mt-6 text-grey">
          <i class="mr-2 wi" style="font-size: 2.3em" :class="[classWI]"></i>
          <p class="font-thin text-2xl">{{ weather.weather[0].description }}</p>
        </div>

        <div class="flex items-center mt-6 text-grey">
          <i class="fas fa-arrow-up mr-2"></i>
          <p class="font-light mr-2 tracking-wide">
            {{ weather.sys.sunrise | moment("h:mm") }} am
          </p>
          <i class="fas fa-arrow-down mr-2"></i>
          <p class="font-light tracking-wide">
            {{ weather.sys.sunset | moment("h:mm") }} pm
          </p>


        </div>

      </div>
      <div class="w-1/2">
        <p class="text-grey text-right font-light" style="font-size:6.8em;">
          {{ Math.round(weather.main.temp) }}&deg;
        </p>
        <div class="text-center">
          Min: {{ weather.main.temp_min }}&deg; | Max: {{ weather.main.temp_max }}&deg;
        </div>
      </div>

    </div>
  </div>

  <!-- <ul v-if="weather">

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
  </ul> -->

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
  },
  computed: {
    classWI: function() {
      if (this.weather != null){
        var weatherID = this.weather.weather[0].id;

        if (weatherID >= 200 && weatherID <= 232) {
          return 'wi-thunderstorm';
        } else if (weatherID >= 300 && weatherID <= 321) {
          return 'wi-sprinkle';
        } else if (weatherID >= 500 && weatherID <= 531) {
          return 'wi-rain';
        } else if (weatherID >= 600 && weatherID <= 622) {
          return 'wi-snow';
        } else if (weatherID >= 701 && weatherID <= 781) {
          return 'wi-train';
        } else if(weatherID == 800) {
          return 'wi-day-sunny';
        } else if (weatherID >= 801 && weatherID <= 804) {
          return 'wi-day-cloudy';
        } else if (weatherID >= 900 && weatherID <= 962) {
          return 'wi-small-craft-advisory';
        }
      }
      return '';
    }
  }
}
</script>
