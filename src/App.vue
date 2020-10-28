<template>
  <v-app>
    <v-content class="ma-4">
      <Test/>
    <div class="d-flex flex-wrap">
      <Footer/>
      <AddNew/>
    </div>
    </v-content>
  </v-app>
</template>

<script>
import Test from './components/Test';
import Footer from './components/Footer';
import AddNew from './components/AddNew';

export default {
  name: 'App',

  components: {
    Test,
    Footer,
    AddNew
  },

  data: () => ({
    //
  }),
};
</script>
