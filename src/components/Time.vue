<template>
  <div class="flex align-center">
    <p style="font-size: 5em;" v-if="currentTime">
      {{ currentTime }}
    </p>
  </div>
</template>


<script>
/* eslint-disable */

import moment from 'moment';

export default {
  name: 'clock',
  data () {
    return {
      currentTime: null
    }
  },
  methods: {
    updateCurrentTime() {
      this.currentTime = moment().format('LTS');
    }
  },
  created() {
    this.currentTime = moment().format('LTS');
    setInterval(() => this.updateCurrentTime(), 1 * 1000);
  }
}


</script>
