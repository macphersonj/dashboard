<template>
  <div>
    <h2>Crypto</h2>
    <ul>
      <li v-for="(price, index) in prices">
        {{ index }}: <span v-for="val in price">{{ val }}</span>
      </li>
    </ul>
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
