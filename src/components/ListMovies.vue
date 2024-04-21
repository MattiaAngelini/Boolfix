<script>
    import { store } from '../store.js'
    
    export default {
        name: 'ListMovie',
        props: {
            cardInfo: Object
        },
        data() {
            return {
                store,
                supportedFlags: [
                    'it',
                    'en',
                    'fr'
                ],
                default_flag:'../src/assets/img/default.jpg',
                
            }
        },
        methods: {
            
            getFlagUrl(language) {
                return new URL(`../assets/img/${language}.jpg`, import.meta.url).href; 
            },

            getLanguageFlagUrl(language) {
                if (this.supportedFlags.includes(language)) {
                    return this.getFlagUrl(language);
                } else {
                    return this.default_flag
                }
            },

            getCoverImageUrl(partialUrl) {
                if(partialUrl){
                    return `https://image.tmdb.org/t/p/w342${partialUrl}`;
                } else {
                    return '../src/assets/img/default.jpg'
                }
                
            },

            convertToFiveStarRating(voto) {           
            const rating = Math.round(voto / 2);
            return rating
            },

        }
    }
</script>

<template>
    <section class="container">
        <div class="d-flex gap-3 justify-content-evenly">
           

            <!--FILM-->
            <ul>
                <h3>Film</h3>
                <li v-for="film in store.movies"> {{ film.title }}</li>
            </ul>
     
            <!-- TITOLO ORIGINALE -->
            <ul>
                <h6>TITOLO ORIGINALE</h6>
                <li v-for="film in store.movies"> {{ film.original_title }}</li>
            </ul>
            <!-- LINGUA -->
            <ul>
                <h6>LINGUA</h6>
                <template v-for="film in store.movies">                              
                    <li> <img :src="getLanguageFlagUrl(film.original_language)"></li>            
                </template>
           </ul>
            <!-- VOTO -->
            <ul>
                <h6>VOTO</h6>
                
                <li v-for="film in store.movies">
                    <template v-for="i in Math.round(convertToFiveStarRating(film.vote_average))">
                                  <i class="fas fa-star"></i> <!-- Stelle piene -->
                    </template>

                    <template v-for="i in Math.floor(5 - Math.round(convertToFiveStarRating(film.vote_average)))">
                                  <i class="far fa-star"></i> <!-- Stelle vuote -->
                    </template>
                </li>
                 
            </ul>
            
            <ul>
                <h6>COPERTINA</h6>
                <li  v-for="poster in store.movies " >
                    <img :src="getCoverImageUrl(poster.backdrop_path)" > 
                </li>               
            </ul>


        </div>
    </section>


    <section class="card">

        

    </section>


</template>



<style scoped lang="scss">
@use '../assets/style/generic' as *;

    li {
        height: 200px;
        padding:20px;
    }

    img {
        width:50px;
    }
</style>
