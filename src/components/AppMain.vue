<script>
import CardMovie from './AppCardMovie.vue'
import CardSeries from './AppCardSeries.vue'
import { store } from '../store'


export default {
    data() {
        return {
          store: store,
        }
    },    
    methods: {
        
    },
    components: {
        CardMovie,
        CardSeries
    },
    created() {
        
    }
}

</script>

<template>

<div class="main-section" v-if="store.send === true">
    <div class="type-content">
        <h1>Film</h1>
    </div>
    <div class="container">
        <div class="row">                
            <CardMovie v-for="infoCard in store.infoFilms" :card="infoCard" />              
                        
        </div>                                   
    </div>
    <div class="type-content">
        <h1>Serie tv</h1>
    </div>
    <div class="container">
        <div class="row">                
            <CardSeries v-for="infoCard in store.infoSeries" :card="infoCard"/>          
                        
        </div>                                   
    </div>
            
</div>    
    

</template>

<style lang="scss" scoped>

.main-section {
    
    background-color: rgb(93, 93, 93);

    .type-content {
        text-align: center;
        padding-top: 50px;
        color: white;
    }
    .container {
        width: 800px;
        margin: 0 auto;
        padding: 50px 0;
    }
    .row {
        display: flex;
        justify-content: center;
        align-items: center;        
        flex-wrap: wrap;
        row-gap: 10px;
    }

   
}



</style>