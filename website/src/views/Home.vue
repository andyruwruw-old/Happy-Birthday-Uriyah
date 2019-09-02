<template>
  <div class="home">
    <div id="background">
      <h1>Happy Birthday Uriyah!</h1>
      <Fireman v-for="fireman in firemen" v-bind:key="fireman.name" v-bind:type="fireman.type" v-bind:x="fireman.x" v-bind:y="fireman.y" v-bind:speed="fireman.speed"
      v-bind:audio="fireman.audio"></Fireman>
      <h2>Click the page and hover over firemen ;)</h2>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Fireman from '@/components/Fireman.vue'

export default {
  name: 'home',
  components: {
    Fireman
  },
  data() {
    return {
      firemen: [],
    }
  },
  methods: {
    move() {
      var media = document.getElementById("music");
      media.volume = .3;
      const playPromise = media.play();
      if (playPromise !== null){
        playPromise.catch(() => { media.play(); })
      }
      for (let i = 0; i < this.firemen.length; i++)
      {
        this.firemen[i].x += this.firemen[i].speed;
        if (this.firemen[i].x > window.innerWidth)
        {
          let newFireman = {type: Math.ceil(Math.random() * 9), x: -150, y: Math.random() * window.innerHeight - 25, name: Math.round(Math.random() * 1000), speed: Math.random() * 5, audio: Math.ceil(Math.random() * 10)};
          this.firemen.splice(i, 1, newFireman);
        }
      }
    }
  },
  created() {
    while(this.firemen.length < 20) {
      let newFireman = {type: Math.ceil(Math.random() * 9), x: Math.random() * window.innerWidth, y: Math.random() * window.innerHeight - 50, name: Math.round(Math.random() * 1000), speed: Math.random() * 3, audio: Math.ceil(Math.random() * 10)};
      this.firemen.push(newFireman);
    }
    setInterval(this.move, 50);
  },
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Bangers&display=swap');

#background {
  display: block;
  position: fixed;
  width: 100vw;
  height: 100vh;
  left: 0px;
  top: 0px;
  background-image: radial-gradient(rgb(0, 0, 0),rgba(0,0,0,0)), url("../assets/background.jpeg");
  background-size: 100% auto;
  background-repeat: repeat;
  background-positon: center;
}

@keyframes title {
  0% {
    font-size: 7em;
  }
    50% {
    font-size: 7.5em;
  }
    100% {
    font-size: 7em;
  }
  
}

h1 {
  color: white;
  z-index: 100;
  display: block;
  width: 100%;
  text-align: center;
  position: fixed;
  top: 10vh;
  font-size: 7em;
  font-family: 'Bangers', cursive;
  background: -webkit-linear-gradient(rgb(255, 232, 128), rgb(119, 21, 21));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: title 2s linear 0s infinite;
}



h2 {
  color: white;
  font-size: 1.5em;
  z-index: 100;
  display: block;
  width: 100%;
  text-align: center;
  position: fixed;
  bottom: 20px;
  
}
</style>
