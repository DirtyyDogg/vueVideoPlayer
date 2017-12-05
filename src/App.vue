<template>

<div id="app">

<videoframe v-bind:currentVideo="currentVideo"></videoframe>

<playlist v-bind:currentVideo="currentVideo" @updateData="swapData($event)"></playlist>

</div>

</template>

<script>

import videoframe from './components/videoFrame'

import playlist from './components/playList'

export default {

  name: 'app',

  components: {

  'videoframe' : videoframe,
  'playlist' : playlist

},

  data () {
    return {
      currentVideo : ''
    }
  },

  methods: {
    swapData: function(data) {
     this.currentVideo = data;
    }
  }
}

</script>

<style scoped>

#app {
  clear : both;
}

</style>
