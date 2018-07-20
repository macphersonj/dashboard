<template>
  <div>
    <h2>News</h2>
    <ul>
      <li v-for="item in news.item">
        {{ item.title[0] }}
      </li>
    </ul>
  </div>
</template>


<script>
/* eslint-disable */

import axios from 'axios'
import xml2js from 'xml2js'
import xml from 'xml-to-json-promise'

var parseString = require('xml2js').parseString;

export default {
  name: 'news',
  data () {
    return {
      news: ''
    }
  },
  mounted () {
  axios
    .get('https://cors-anywhere.herokuapp.com/https://www.news.com.au/content-feeds/latest-news-national/')
    .then(response => {
       var self = this;
       parseString(response.data, function (err, result) {
         self.news = result.rss.channel[0]
       });
     })
   }
}
</script>
