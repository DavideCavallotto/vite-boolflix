<script>
import { store } from '../store'

export default {
    data() {
        return {
          store: store
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
    width: 150px;
    height: 200px;
    background-color: antiquewhite;
    border-radius: 20px;
    padding: 30px;
}

</style>