<template>
    <div class="container">
        <img src="../assets/game-over.png">
        <button @click="restart()">Restart</button>
    </div>
</template>

<script>
export default {
    methods: {
        restart() {
            location.reload();
        }
    }
}
</script>

<style scoped>
    img {
        height: 80vh;
        position: absolute;
        top: 50%;
        left: 50;
        transform: translate(-50%, -50%);
    }
    button {
        /* background-color: greenyellow; */
        background-image: linear-gradient(red, white);
        padding: 10px;
        border: 10px solid black;
        border-radius: 5px;
        font-size: 40px;

        position: absolute;
        top: 50%;
        left: 50;
        transform: translate(-50%, -50%);
        z-index: 10;
    }
</style>