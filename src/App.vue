<template>
  <GameOver v-if="isGameOver"></GameOver>
  <div class="playground" v-else>
    <!-- <p>{{  balloons  }}</p> -->
    <LifesComponent :life="life"></LifesComponent>
    <ArcheryComponent :archeryPosition="archeryPosition"></ArcheryComponent>
    <BalloonComponent v-for="(balloon, index) in balloons" :key="index" :x="balloon.x" :y="balloon.y"></BalloonComponent>
    <ArrowComponent v-for="(arrow, index) in arrows" :key="index" :x="arrow.x" :y="arrow.y"></ArrowComponent>
  </div>
</template>

<script>
import BalloonComponent from './components/BalloonComponent.vue'
import ArcheryComponent from './components/ArcheryComponent.vue'
import LifesComponent from './components/LifesComponent.vue'
import ArrowComponent from './components/ArrowComponent.vue'
import GameOver from './components/GameOver.vue'

export default {
  name: 'App',
  components: {
    BalloonComponent,
    ArcheryComponent,
    LifesComponent,
    ArrowComponent,
    GameOver,
  },
  data() {
    return {
      x: 10,
      y: 10,
      life: 5,
      isGameOver: false,
      archeryPosition: 20,
      balloons: [],
      arrows: []
    }
  },
  mounted() {
    let self = this;

    window.addEventListener('keyup', function (ev) {
      self.keyup(ev); // declared in your component methods
    });

    setInterval(() => {
      const newBallon = { x: this.randomNumber(20, 95), y: 90 };
      this.balloons.push(newBallon);
    }, 3000);

    const FPS = 4;

    const interval = setInterval(() => {
      this.updatePositons();
      this.detectCollusion();
      if (this.life == 0) {
        this.isGameOver = true;
        const audio = new Audio(require('./assets/game-over.mp3'));
        audio.play();
        clearInterval(interval);
      }
    }, 1000 / FPS);
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
        case 'Space': this.addArrow(); break;
      }
    },
    addArrow() {
      const newArrow = { x: 2, y: this.archeryPosition };
      this.arrows.push(newArrow);
    },
    updatePositons() {
      this.balloons.forEach(balloon => {
        balloon.y -= 2;
        if (balloon.y == 0) {
          this.life--;
          const audio = new Audio(require('./assets/life-loss.wav'));
          audio.play();
        }
      })
      this.balloons = this.balloons.filter(balloon => balloon.y > 0);

      this.arrows.forEach(arrow => {
        arrow.x += 5;
      })
      this.arrows = this.arrows.filter(arrow => arrow.x < 100);
    },
    detectCollusion() {
      this.arrows.forEach(arrow => {
        this.balloons.forEach((balloon, index, array) => {
          const accuracy = 6;
          if (Math.abs(balloon.x - arrow.x) < accuracy && Math.abs(balloon.y - arrow.y) < accuracy) {
            array.splice(index, 1);
            const audio = new Audio(require('./assets/popup-sound.wav'));
            audio.play();
          }
        })
      })
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