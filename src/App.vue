<template>
  <div id="app">
    <div class="container mx-auto px-4">
      <div class="flex flex-col lg:flex-row">
        <div class="w-full lg:w-1/2 bg-grey p-10">
          <clock></clock>
        </div>

        <div class="w-full lg:w-1/2 bg-grey-light p-10">
          <weather></weather>
        </div>
      </div>

      <div class="flex flex-col lg:flex-row">
        <div class="w-full lg:w-1/2 bg-grey-light p-10">
          <news></news>
        </div>
        <div class="w-full lg:w-1/2 bg-grey p-10">
          <crypto></crypto>
          <cryptoGraph></cryptoGraph>

        </div>
      </div>

    </div>
  </div>
</template>

<script>

import '@/assets/styles/main.css'

/* eslint-disable */

import news from './components/News.vue'
import weather from './components/Weather.vue'
import crypto from './components/Crypto.vue'
import clock from './components/Time.vue'
import cryptoGraph from './components/CryptoGraph.vue'

export default {
  name: 'App',
  components: {
    news,
    weather,
    crypto,
    clock,
    cryptoGraph
  }
}

</script>
