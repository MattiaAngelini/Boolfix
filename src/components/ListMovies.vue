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
                return `https://image.tmdb.org/t/p/w342${partialUrl}`;
            }


        }
    }
</script>

<template>
    <section class="container">
        <div class="d-flex gap-3 justify-content-evenly">
            <ul>
                <h3>Film</h3>
                <li v-for="film in store.movies"> {{ film.title }}</li>
            </ul>
            <!-- TITOLO ORIGINALE -->
            <ul>
                <h3>TITOLO ORIGINALE</h3>
                <li v-for="film in store.movies"> {{ film.original_title }}</li>
            </ul>
            <!-- LINGUA -->
            <ul>
                <h3>LINGUA</h3>
                <template v-for="film in store.movies">                              
                    <li> <img :src="getLanguageFlagUrl(film.original_language)"></li>            
                </template>
           </ul>
            <!-- VOTO -->
            <ul>
                <h3>VOTO</h3>
                <li v-for="film in store.movies"> {{ film.vote_average }}</li>
            </ul>
            
            <ul>
                <h3>COPERTINA</h3>
                <li  v-for="poster in store.movies" >
                    <img :src="getCoverImageUrl(poster.poster_path)" > 
                </li>
            </ul>
        </div>
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
