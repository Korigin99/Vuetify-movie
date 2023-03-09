<template>
  <v-app>
    <v-main>
      <LoginSection/>
    </v-main>
  </v-app>
</template>

<script>
import LoginSection from './components/LoginSection.vue'

export default {
  name: 'App',

  components: {
    LoginSection
  },

  data: () => ({
    //
  }),
}
</script>
<style scoped>
  /*@import url(./assets/reset.css);*/
</style>
