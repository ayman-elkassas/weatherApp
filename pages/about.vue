<template>
  <div>
    <h3>{{title}}</h3>
<!--    <router-link to="/">Home</router-link>-->
    <nuxt-link to="/">Home</nuxt-link>
<!--    //OR-->
<!--    <n-link to="/">Home</n-link>-->
<!--    <NuxtLink to="/">Home</NuxtLink>-->
<!--    <NLink to="/">Home</NLink>-->
  </div>
</template>

<script>
  export default {
    name : 'about' ,
    middleware:'test',
    asyncData(){
      return {
        title:'about'
      }
    },
    // data(){
    //   return {
    //     title:'AA'
    //   }
    // },
    //Todo:head to insert in head page any thing (js or css files as example)
    head :function() {
      return{
        title:'About',
        meta:[
          {
            hid:'description',
            name:'description',
            content:'Amazing About Page'
          }
        ],
        script:[
          {src:'/about.js'}
        ]
      }
    }
  }
</script>

<style scoped>

</style>
