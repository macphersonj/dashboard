  <div>
    <ul>
      <li v-for="data in prices.Data">
        {{ data.time | moment("dddd, MMMM Do YYYY")  }} | {{ data.close }}
      </li>
    </ul>

    <ul>
      <li v-for="data in prices.Data">
        {{ data.close }}
      </li>
    </ul>
    <!-- <chart></chart> -->
  </div>

<script>
/* eslint-disable */

import axios from 'axios'
import moment from 'moment'
import chart from './graphs/Chart.js'
import VueCharts from 'vue-chartjs'
import { Line } from 'vue-chartjs'

export default {
  extends: Line,
  name: 'cryptoGraph',
  data () {
    return {
      prices: '',
      plotArray: [],
      plotLabel: []

    }
  },
  components: {
    chart
  },
  methods: {
    consoleOne: function() {
      var i;
      for (i = 0; i < this.prices.Data.length; i++) {
        var close = this.prices.Data[i];
        this.plotArray.push(close.close);
        this.plotLabel.push(close.time);

      }
    },
    getCrypto: function() {
      axios
        .get('//min-api.cryptocompare.com/data/histoday?fsym=XRP&tsym=AUD&limit=10&aggregate=3&e=CCCAGG')
        .then(
          response => (
            this.prices = response.data,
            this.consoleOne(),
            this.renderChart({
              labels: this.plotLabel,
              datasets: [
                {
                  label: 'XRP Price Data',
                  borderColor: '#FC2525',
                  data: this.plotArray,
                }
              ]
            })
          )
      )
    }
  },
  created() {
    this.getCrypto()
  }
}
</script>
