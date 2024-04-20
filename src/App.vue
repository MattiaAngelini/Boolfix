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
    ListMovies,
  },
  
  // DATA
  data() {
    return {
      store
    };
  },
  
  // METHODS
  methods: {  


    searchFilmsAndSeries() {
      this.getSeriesFromApi();
      this.getMoviesFromApi();  
      this.getPosterFilmFromApi();
      this.getPosterSeriesFromApi()
    },
    
    
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
        store.movies = response.data.results
        
      });
    },

    getSeriesFromApi() {  
      //URL search movie 
      let apiUrl = 'https://api.themoviedb.org/3/search/tv';
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
        store.series = response.data.results
        
      });
    },

    
    getPosterFilmFromApi() {  
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
        store.posterMovies = response.data.results.map(result => result.backdrop_path);
        
      });
    },

    
    getPosterSeriesFromApi() {  
      //URL search movie 
      let apiUrl = 'https://api.themoviedb.org/3/search/tv';
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
        store.posterSeries =  response.data.results.map(result => result.backdrop_path);
        
      });
    },

  },
  
  // MOUNTED
  mounted() {
    //
  }

};
</script>


//TEMPLATE
<template>
    <AppHeader></AppHeader>
    <AppSearch  @searchFilm=" searchFilmsAndSeries"></AppSearch>
    <ListMovies></ListMovies>
</template>


//STYLE
<style scoped lang="scss">
@use '../src/assets/style/generic' as *;


</style>
