<template>
  <v-app>
    <v-content class="ma-4">
      <Test/>
    </v-content>
  </v-app>
</template>

<script>
import Test from './components/Test';

export default {
  name: 'App',

  components: {
    Test,
  },

  data: () => ({
    //
  }),
};
</script>
