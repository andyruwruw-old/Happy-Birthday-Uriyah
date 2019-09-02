<template>
  <div class="fireman">
    <div @mouseover="noise" v-bind:class="{fireman1 : type == 1, fireman2 : type == 2, fireman3 : type == 3, fireman4 : type == 4, fireman5 : type == 5, fireman6 : type == 6, 
    fireman7 : type == 7, fireman8 : type == 8, fireman9 : type == 9}" v-bind:style="{left: x + 'px', top: y + 'px', zIndex: speed}" id="image">
    </div>
  </div>
</template>

<script>
export default {
  name: 'fireman',
  props: {
    type: Number,
    name: Number,
    x: Number,
    y: Number,
    speed: Number,
    audio: Number,
  },
  methods: {
    noise() {
      var media = document.getElementById(this.audio);
      media.volume = .5;
      const playPromise = media.play();
      if (playPromise !== null) playPromise.catch(() => {media.play();});
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#image {
  display: block;
  height: 56vh;
  width: 15vw;
  background-size: 100% auto;
  background-repeat: no-repeat;
  background-position: center;
  position: fixed;
  transition: all .2s ease;
  opacity: .5;
}
@keyframes shake {
  0% {
    transform: rotate(0deg) scale(1 1);
  }
  25% {
    transform: rotate(2deg) scale(1.05 1.05);
  }
  50% {
    transform: rotate(0deg) scale(1.1 1.1);
  }
  75% {
    transform: rotate(-2deg) scale(1.15 1.15);
  }
  100% {
    transform: rotate(0deg) scale(1.2 1.2);
  }
}

#image:hover {
  transform: scale(1.2, 1.2);
  animation: shake .5s ease;
  opacity: 1;
}

.fireman1 {
  background-image: url("../assets/fireman1.png");
}

.fireman2 {
  background-image: url("../assets/fireman2.png");
}

.fireman3 {
  background-image: url("../assets/fireman3.png");
}

.fireman4 {
  background-image: url("../assets/fireman4.png");
}

.fireman5 {
  background-image: url("../assets/fireman5.png");
}

.fireman6 {
  background-image: url("../assets/fireman6.png");
}

.fireman7 {
  background-image: url("../assets/fireman7.png");
}

.fireman8 {
  background-image: url("../assets/fireman8.png");
}

.fireman9 {
  background-image: url("../assets/fireman9.png");
}
</style>
