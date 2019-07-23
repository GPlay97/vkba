<template>
  <v-app dark>
    <toolbar />
    <v-content>
      <router-view />
      <page-footer />
    </v-content>
  </v-app>
</template>

<script>
import toolbar from './components/Toolbar.vue';
import footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    toolbar,
    'page-footer': footer
  },
  data () {
    return {
      //
    }
  }
}
</script>
