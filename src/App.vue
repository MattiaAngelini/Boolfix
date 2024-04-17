<script>
import axios from 'axios';
import { store } from './store.js'; 
import AppHeader from './components/AppHeader.vue';
import AppSearch from './components/AppSearch.vue';
import ListMovies from './components/ListMovies.vue';

export default {
  //COMPONENTS
  components: {
    AppHeader,
    AppSearch,
    ListMovies

  },
  //DATA
  data() {
    return {
      store
    };
  },

};
</script>

<template>
  
  <AppHeader></AppHeader>
  <AppSearch></AppSearch>
  <ListMovies></ListMovies>

</template>

<style scoped lang="scss">

</style>
