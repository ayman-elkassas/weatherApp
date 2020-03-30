<template>
  <div>
    <h3>I am a blog post</h3>
    <h3>My Route is : {{slug.post}}</h3>
  </div>
</template>

<script>
  //TODO:NOTE -> if component name start with (_) any route name call it...
  export default {
    name : 'blog',
    validate({params}){
      //TODO:Forward if route is decimal otherwise forward to error page
      return /^\d+$/.test(params.post)
    },
    data(){
      return {
        slug:this.$route.params
      }
    },
    created () {
      console.log(this.$route.params)
    }
  }
</script>

<style scoped>

</style>
