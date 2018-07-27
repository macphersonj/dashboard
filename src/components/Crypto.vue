<template>
  <div>
    <h2>Crypto</h2>
    <div class="flex flex-col lg:flex-row mt-8">
      <div v-for="(price, index) in prices" class="w-1/3 p-2">
        <div class="max-w-sm rounded overflow-hidden shadow-lg bg-white py-4 px-2 text-center">
          <h3 class="text-1xl mb-4">{{ index }}</h3>
          <span v-for="val in price">${{ val }}<br />AUD</span>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */

import axios from 'axios'


export default {
  name: 'crypto',
  data () {
    return {
      prices: ''
    }
  },
  mounted () {
  axios
    .get('//min-api.cryptocompare.com/data/pricemulti?fsyms=XRP,XLM,LTC&tsyms=AUD')
    .then(response => (this.prices = response.data))
   }
}
</script>
