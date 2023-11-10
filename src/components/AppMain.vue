<script>
import CardMovie from './AppCardMovie.vue'

export default {
    data() {
        return {
          
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
<div class="main-section">
        <div class="container">
            <div class="row">
                <div class="col-4" v-for="card in 4">
                    <CardMovie/>

                </div>
                
                
            </div>                
            
            
            
        </div>
            
    </div>    
    

</template>

<style lang="scss" scoped>

.main-section {
    height: 1000px;
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
        gap: 10px;
    }

    .col-4 {
        flex-basis: calc((100% / 12) * 4);
    }
}



</style>