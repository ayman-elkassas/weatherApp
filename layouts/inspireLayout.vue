<template>
    <div>
      <h3>{{title}}</h3>
      <nuxt></nuxt>
    </div>
</template>

<script>
  export default {
    name : 'inspireLayout',
    data:function() {
      return {
        title:'I am for inspire only'
      }
    }
  }
</script>

<style scoped>

</style>
