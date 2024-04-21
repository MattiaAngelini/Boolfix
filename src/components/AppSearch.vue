<script>

import { store } from '../store.js'

export default {
    name: 'AppSearch',

    data() {
    return {
        store,
        
    };
    },
}

</script>

<template>

    <label class="p-4">
        <!--VARIABILE SCELTA UTENTE SALVATA IN STORE-->
        <input v-model="store.userSearchMovies" type="text" name="" id="">
        <!--BUTTON CON EMIT COLLEGATO AD APP VUE DOVE HO FUNZIONI-->
        <button @click="$emit('searchFilm')">CERCA</button>
    </label>

</template>

<style scoped lang="scss"> 
@use '../assets/style/generic' as *;

</style>


