<template>
    <div class="lifes">
        <img v-for="index in life" :key="index" src="../assets/heart.png">
        <img v-for="index in total - life" :key="index" src="../assets/heart-dead.png">
    </div>
</template>

<script>
export default {
  props: ['life'],
  data() {
    return {
        total: 5
    }
  }
}
</script>


<style>
.lifes {
    position: absolute;
    transition: all .2s;
    height: 4%;
}
.lifes img {
    height: 100%;
    margin-left: 5px;
}
</style>