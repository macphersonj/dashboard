<template>
  <div id="app">
    <div class="container mx-auto px-4">
      <div class="flex mb-4">
        <div class="w-1/2 bg-grey-light p-10">
          <news></news>
        </div>
        <div class="w-1/2 bg-grey p-10">
          <weather></weather>
        </div>
      </div>
      <!-- <crypto></crypto> -->
    </div>
  </div>
</template>

<script>

import '@/assets/styles/main.css'

/* eslint-disable */

import news from './components/News.vue'
import weather from './components/Weather.vue'
import crypto from './components/Crypto.vue'

export default {
  name: 'App',
  components: {
    news,
    weather,
    crypto
  }
}

</script>
