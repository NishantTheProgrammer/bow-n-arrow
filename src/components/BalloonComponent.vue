<template>
    <p>balloon {{ x }} {{ y }}</p>
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