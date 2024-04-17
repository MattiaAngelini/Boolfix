<script>
import axios from 'axios';
import { store } from './store.js'; 
import AppHeader from './components/AppHeader.vue';
import AppSearch from './components/AppSearch.vue';
import ListMovies from './components/ListMovies.vue';

export default {
  // COMPONENTS
  components: {
    AppHeader,
    AppSearch,
    ListMovies
  },
  
  // DATA
  data() {
    return {
      store
    };
  },
  
  // METHODS
  methods: {  
    //funzione collegata con $emit a AppSearch (button)
    getMoviesFromApi() {  
      //URL search movie 
      let apiUrl = 'https://api.themoviedb.org/3/search/movie';
      //api key e query con scelta utente
      const queryParams = {
        api_key: '3a857f85c270c76928309334dc033755',
        query: store.userSearchMovies
      };
      
      //chiamata axios con parametri query params
      axios.get(apiUrl,
      {params: queryParams}
    )
    //risultato chiamata pushato in store.films
      .then((response) => {  
        store.films = response.data.results
        
      });
    },
  },
  
  // MOUNTED
  mounted() {
  }
};
</script>


//TEMPLATE
<template>
    <AppHeader></AppHeader>
    <AppSearch  @searchFilm="getMoviesFromApi"></AppSearch>
    <ListMovies></ListMovies>
</template>


//STYLE
<style scoped lang="scss">
@use '../src/assets/style/generic' as *;


</style>
