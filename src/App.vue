<template>
  <v-app style="background: rgba(36, 101, 138, 0.527)">
    <NavBar/>
    <router-view/>
    <FooterTarefa/>
  </v-app>
</template>


<script>
import NavBar from './components/navbar/NavBar.vue';
import FooterTarefa from './components/footer/FooterTarefa.vue';

export default {
  name: 'App',
  components:{
    NavBar,
    FooterTarefa,
}
}
</script>


