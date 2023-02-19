<template>
    <img class="balloon" :style="{ top: y + '%', left: x + '%' }" src="../assets/balloon.png">
</template>



<script>
export default {
    props: ['x', 'y'],
    created() {
        // props are exposed on `this`

    }
}
</script>

<style scoped>
.balloon {
    height: 10%;
    position: absolute;
    /* transition: all 1s; */
}
</style>