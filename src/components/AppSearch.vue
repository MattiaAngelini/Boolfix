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

    <input v-model="store.searchMovies" type="text" name="" id="">
    <button>CERCA</button>
  
</template>

<style scoped lang="scss"> 
@use '../assets/style/generic' as *;

</style>


