<template>
    <p class="balloon" :style="{ zIndex: 2, top: y + '%', left: x + '%' }">{{ x }},{{ y }}</p>
    <img class="balloon" :style="{ top: y + '%', left: x + '%' }" src="../assets/balloon.png">
</template>



<script>
export default {
    props: ['x', 'y'],
    created() {
        // props are exposed on `this`
        console.log(this.x, this.y)

    }
}
</script>

<style>
.balloon {
    height: 10%;
    position: absolute;
    transition: all .2s;
}
</style>