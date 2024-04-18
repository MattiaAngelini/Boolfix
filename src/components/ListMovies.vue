<script>

import { store } from '../store.js'

export default {
    name: 'ListMovie',
 

    data() {
    return {
        store,
        
    };
    },
}


</script>

<template>
    
    <!--TITOLO-->

    <section class="container">

        <div class="d-flex gap-3 justify-content-evenly">
            <ul>
                <h3>Film</h3>
                <li v-for="film in store.movies"> {{ film.title }}</li>
            </ul>

            <!--TITOLO ORIGINALE-->
            <ul>
                <h3>TITOLO ORIGINALE</h3>
                <li v-for="film in store.movies"> {{ film.original_title }}</li>
            </ul>

            <!--LINGUA-->
            <ul>
                <h3>LINGUA</h3>
                <li v-for="film in store.movies"> {{ film.original_language  }}</li>
            </ul>

            <!--VOTO-->
            <ul>
                <h3>VOTO</h3>
                <li v-for="film in store.movies"> {{ film.vote_average }}</li>
            </ul>
        </div>
    
    </section>
  
</template>

<style scoped lang="scss">
@use '../assets/style/generic' as *;


</style>