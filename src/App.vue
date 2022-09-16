<template>

  <v-app>
    
    <v-main>
      <cmp_menu></cmp_menu>  
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import cmp_menu from '@/components/cmp_menu.vue';
export default {
  name: 'App',
  components: {
    cmp_menu
},

  data: () => ({
    //
    drawer: false,
      group: null,
  }),
  watch: {
      group () {
        this.drawer = false
      },
    },
};
</script>
