<template>
  <div>
    <v-toolbar extension-height="">
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>{{title}}</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <n-link to="/"><v-icon>mdi-home</v-icon></n-link>
      </v-btn>

      <v-btn icon>
        <span><n-link to="/about"><v-icon>mdi-dots-horizontal</v-icon></n-link></span>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>

    <nuxt></nuxt>
  </div>


</template>

<script>
export default {
  data:function() {
    return {
      title:'Nuxt List'
    }
  }
  // data () {
  //   return {
  //     clipped: false,
  //     drawer: false,
  //     fixed: false,
  //     items: [
  //       {
  //         icon: 'mdi-apps',
  //         title: 'Welcome',
  //         to: '/'
  //       },
  //       {
  //         icon: 'mdi-chart-bubble',
  //         title: 'Inspire',
  //         to: '/inspire'
  //       }
  //     ],
  //     miniVariant: false,
  //     right: true,
  //     rightDrawer: false,
  //     title: 'Vuetify.js'
  //   }
  // }
}
</script>

<style scoped>

</style>
