<template>
  <v-app>
    <v-app-bar
      app
      dark
    >
    <v-spacer/>
    <h2>My Calculator</h2>
    <v-spacer/>
    </v-app-bar>
    <v-main class="grey darken-3">
      <v-container fluid class="d-flex justify-center mt-8">
        <Calculator/>
      </v-container>
    </v-main>
    <v-footer padless class="grey darken-4 white--text">
      <v-col class="text-center" col="12">
        Created by <strong>Rakibul Hasan</strong>
      </v-col>

    </v-footer>
    
  </v-app>
</template>

<script>
import Calculator from './components/Calculator';

export default {
  name: 'App',

  components: {
    Calculator,
  },

  data: () => ({
    //
  }),
};
</script>
<style>
.class {
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
