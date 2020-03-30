<template>
    <v-app>
      <v-content>
        <v-toolbar dark color="indigo">
          <v-app-bar-nav-icon></v-app-bar-nav-icon>

          <v-toolbar-title>{{title}}</v-toolbar-title>

          <v-spacer></v-spacer>

          <v-toolbar-items class="hidden-sm-and-down">

            <v-btn style="background: none">
              <n-link to="/weather-app">Weather App</n-link>
            </v-btn>

          </v-toolbar-items>
        </v-toolbar>
        <transition>
          <nuxt></nuxt>
        </transition>

      </v-content>

    </v-app>

</template>

<script>
export default {
  data:function() {
    return {
      title:'Weather App'
    }
  }
}
</script>

<style scoped>
  a{
    text-decoration: none;
    color: white;

  }
</style>
