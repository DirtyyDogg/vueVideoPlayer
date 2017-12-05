<template>

<div id="videoframe">

<div id="border">

<video id="video" ref="video" width="100%" height="100%" controls>

  <source v-bind:src="currentVideo">

Your browser does not support the video tag.

</video>

<div id="controls" @click="videoFunction">

<button>Play</button>
<button>Pause</button>

</div>

</div>
</div>

</template>

<script>

import { bus } from '../main';

export default {
  name: 'video-frame',

props : {
 
 currentVideo: {
  type : String
 }

  },
  data () {
    return {

    }
  },
  methods: {
    videoFunction: function(e){

      let value = e.target.innerText;

      switch(value) {

        case "Play" : {
            this.$refs.video.play();
              break;
        }

        case "Pause" : {
              this.$refs.video.pause();
              break;              
        }
      }

    }
  },
  created(){

    bus.$on('reload', () => {

      this.$refs.video.load();     
      this.$refs.video.play();

    })
  }
}
</script>

<style>

#border {
    background: url('https://ak1.picdn.net/shutterstock/videos/21586321/thumb/1.jpg') center no-repeat;
    background-size: cover;
    border: 10px solid black;
    border-radius: 15px;
    margin: 2rem 0.5rem;
    height: 30rem;
    width: 55%;
    float: left;
}

#controls {
  border: 10px solid white;
  border-radius: 15px;
  background: black;
  height: 5em;
}

#controls button {
  border:none;
  color: white;
  background: #172951;
  padding: 0.5em 3em;
  margin: 0.8em 6em;
  border-radius: 5px;
  font-size: 1em;
}

#video {

height: 100%;
width: 100%;

}

</style>
