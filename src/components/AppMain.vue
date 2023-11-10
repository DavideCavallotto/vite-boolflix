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
        CardMovie
    },
    created() {
        
    }
}

</script>

<template>
<div class="main-section" v-if="store.send === true">
        <div class="container">
            <div class="row">                
                <CardMovie v-for="infoCard in store.infoFilms" :card="infoCard" />               
                
                
            </div>                
            
            
            
        </div>
            
    </div>    
    

</template>

<style lang="scss" scoped>

.main-section {
    
    background-color: rgb(93, 93, 93);

    .container {
        width: 800px;
        margin: 0 auto;
        padding-top: 100px;
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