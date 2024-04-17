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

    <input v-model="store.userSearchMovies" type="text" name="" id="">
    <button @click="$emit('searchFilm')">CERCA</button>
  
</template>

<style scoped lang="scss"> 
@use '../assets/style/generic' as *;

</style>


