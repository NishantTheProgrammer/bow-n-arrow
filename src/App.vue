<template>
  <div class="playground">
    <ArcheryComponent :archeryPosition="archeryPosition"></ArcheryComponent>
    <BalloonComponent v-for="(balloon, index) in balloons" :key="index" :x="balloon.x" :y="balloon.y"></BalloonComponent>
  </div>
</template>

<script>
import BalloonComponent from './components/BalloonComponent.vue'
import ArcheryComponent from './components/ArcheryComponent.vue'

export default {
  name: 'App',
  components: {
    BalloonComponent,
    ArcheryComponent
  },
  data() {
    return {
      x: 10,
      y: 10,
      archeryPosition: 20,
      balloons: []
    }
  },
  mounted() {
    let self = this;

    window.addEventListener('keyup', function (ev) {
      self.keyup(ev); // declared in your component methods
    });

    setInterval(() => {
      const newBallon = { x: this.randomNumber(20, 95), y: 85 };
      this.balloons.push(newBallon);
    }, 3000)
  },
  methods: {
    increseByTen() {
      this.counter += 10;
    },
    randomNumber(min, max) {
      return Math.floor(Math.random() * (max - min) + min);
    },
    keyup(ev) {
      switch (ev.code) {
        case 'ArrowDown': this.archeryPosition += 10; break;
        case 'ArrowUp': this.archeryPosition -= 10; break;
      }
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

body {
  background-color: black;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.playground {
  background-color: white;
  height: 80vh;
  width: 80vw;
  border-radius: 20px;
  padding: 30px;
  position: relative;
}
</style>