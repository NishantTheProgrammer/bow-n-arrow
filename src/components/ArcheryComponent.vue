<template>
    <img class="archery" :style="{  top: archeryPosition + '%' }" src="../assets/archery.png" >
</template>


<script>
export default {
  props: ['archeryPosition'],
  created() {
    // props are exposed on `this`
    
  }
}
</script>


<style scoped>
.archery {
    height: 12%;
    position: absolute;
    /* transition: all .2s; */
}
</style>