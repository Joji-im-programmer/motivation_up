<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      ごきげんよう!!
    </v-app-bar>
    <v-main>
      <Motivation/>
    </v-main>
  </v-app>
</template>

<script>
import Motivation from './components/Motivation';

export default {
  name: 'App',

  components: {
    Motivation,
  },

  data: () => ({
    //
  }),
};
</script>
