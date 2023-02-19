<template>
  <div class="playground">
    <ArcheryComponent :archeryPosition="archeryPosition"></ArcheryComponent>
  </div>
  <BalloonComponent :x="x" :y="y"></BalloonComponent>
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
      x: 100,
      y: 400,
      archeryPosition: 20
    }
  },
  mounted() {
    let self = this; 

    window.addEventListener('keyup', function(ev) {
        self.keyup(ev); // declared in your component methods
    });
  },
  methods: {
    increseByTen() {
      this.counter += 10;
    },
    keyup(ev) {
      switch(ev.code) {
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