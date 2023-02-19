<template>
    <img class="arrow" :style="{ top: y + '%', left: x + '%' }" src="../assets/arrow.png">
</template>



<script>
export default {
    props: ['x', 'y'],
    created() {
    },
    mounted() {
        const audio = new Audio(require('../assets/arrow-sound.mp3'));
        audio.play();
    }
}
</script>

<style scoped>
.arrow {
    height: 12%;
    position: absolute;
    /* transition: all 1s; */
}
</style>