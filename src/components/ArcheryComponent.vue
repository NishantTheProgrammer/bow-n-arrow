<template>
    <img class="archery" :style="{  top: archeryPosition + '%' }" src="../assets/archery.png" >
</template>


<script>
export default {
  props: ['archeryPosition'],
  created() {
    // props are exposed on `this`
    console.log(this.x, this.y)
    
  }
}
</script>


<style>
.archery {
    height: 12%;
    position: absolute;
    transition: all .2s;
}
</style>