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
  

    <section class="ms-cards">

            <ul>        
                <li  v-for="film in store.movies " >

                    <img class="ms-card" :src="getCoverImageUrl(film.backdrop_path)" >  
                        
                    <section>
                        <div> TITOLO: {{ film.title }}</div>   
                            <div>LINGUA: <img class="flag" :src="getLanguageFlagUrl(film.original_language)"></div>     
                        
                        <div class="d-flex"> VOTO :                
                            <div v-for="i in Math.round(convertToFiveStarRating(film.vote_average))">
                                            <i class="fas fa-star"></i> <!-- Stelle piene -->
                            </div>
                            <div v-for="i in Math.floor(5 - Math.round(convertToFiveStarRating(film.vote_average)))">
                                            <i class="far fa-star"></i> <!-- Stelle vuote -->                
                            </div>
                        </div>
                   </section>  

                </li>     
                          
            </ul>
    </section>


</template>


<style scoped lang="scss">
@use '../assets/style/generic' as *;

 

    .ms-cards{

        ul{ 
             display: flex;
             overflow-x: auto;  

                li {
                    position: relative;
                    padding: 30px;
                    line-height: 40px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    font-size: 18px;
                    font-weight: 700;
                
                        section {
                            display: none;
                            position: absolute;   
                            width: 300px;    
                            height: 300px;   
                                   
                        }

                        &:hover section{
                            display: block;
                            background-color: rgba(0,0,0,0.8);
                            color: white;
                        }

                        
                }
                
        }

        img {
            width: 300px;
            height: 300px;
            
        }

        .flag {
            width: 60px;
            height: 30px;
        }

      
      

    }


</style>
