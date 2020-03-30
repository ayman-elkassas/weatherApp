<template>
  <div>
    <h3>This is error page</h3>
    <h3>{{error.statusCode}} not found</h3>
  </div>
</template>

<script>
export default {
  layout: 'error-layout',
  props:{
    error:{
      type:Object,
      default:null
    }
  }
}
</script>

<style scoped>
h1 {
  font-size: 20px;
}
</style>
