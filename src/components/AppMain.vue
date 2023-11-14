<script>
import CardMovie from './AppCardMovie.vue'
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
    <div class="container tv-container">
        <div class="row">                
            <CardMovie v-for="infoCard in store.infoSeries" :card="infoCard"/>          
                        
        </div>                                   
    </div>
            
</div>    
    

</template>

<style lang="scss" scoped>

.main-section {    
    overflow: auto;
    height: 100vh;
    background-color: #282B69;

    .type-content {
        text-align: center;
        padding-top: 50px;
        color: #282B69;

        h1 {
            -webkit-text-stroke: 0.8px #E92088;
            font-size: 50px;
        }
    }
    .container {
        width: 1024px;
        margin: 0 auto;
        padding: 50px 0;
    }

    .tv-container {
        padding-bottom: 150px;
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