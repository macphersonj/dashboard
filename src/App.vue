<template>
  <div id="app">
    <news></news>
    <weather></weather>
    <crypto></crypto>
  </div>
</template>

<script>

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
