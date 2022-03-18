<template>
  <v-app dark>
    <v-app-bar
      :clipped-left="clipped"
      color="#27D3EB"
      fixed
      app
    >
      <v-toolbar-title  ><h1>my<strong>Translate</strong></h1></v-toolbar-title>
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false
    }
  }
}
</script>

<style scoped>
/* change v-app-bar to #27D3EB */
.v-app-bar {
  color: #fff;
}
</style>
