<script>
import { store } from '../store'

export default {
    data() {
        return {
          store: store,
          src: 'https://image.tmdb.org/t/p/w185'
        }
    },    
    methods: {
        
    },
    components: {
        
    },
    created() {
        
    }
}

</script>

<template>
    <div class="card">
        <img :src='src + store.infoFilms[0].poster_path' alt="">
        <p class="title">
            {{ store.infoFilms[0].original_title }}
        </p>
        <p class="original-title">
            Titolo originale
        </p>
        <p class="language">
            Lingua
        </p>
        <p class="vote">
            Voto
        </p>

    </div>

    

</template>

<style lang="scss" scoped>
.card {
    
    background-color: antiquewhite;
    border-radius: 20px;
    padding: 30px;
}

</style>