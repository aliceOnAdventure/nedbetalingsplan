<template>
  <v-app>
    <v-app-bar
      app
      color="rgb(135, 42, 34)"
      dark
    >
    <div class="d-flex align-center">
        Nedbetalingsplan
      </div>
    </v-app-bar>

    <v-main>
      <Brukerinput/>
      <!-- <Tabell/> -->
    </v-main>
  </v-app>
</template>

<script>
import Brukerinput from './components/Brukerinput';
export default {
  name: 'App',

  components: {
    Brukerinput,
  },

  data: () => ({
    //
  }),
};
</script>
