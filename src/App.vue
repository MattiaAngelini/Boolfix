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
    getMoviesFromApi() {  
      let apiUrl = 'https://api.themoviedb.org/3/search/movie';
      
     
      const queryParams = {
        api_key: '3a857f85c270c76928309334dc033755',
        query: 'results'
      };

      axios.get(apiUrl,
      {params: queryParams}
    )
      .then((response) => {  
       
        store.films = response.data.results
        
      });
    },
  },
  
  // MOUNTED
  mounted() {
    this.getMoviesFromApi();
  }
};
</script>


//TEMPLATE
<template>
    <AppHeader></AppHeader>
    <AppSearch></AppSearch>
    <ListMovies></ListMovies>
</template>


//STYLE
<style scoped lang="scss">

</style>
