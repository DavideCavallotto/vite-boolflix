<script>
import { store } from '../store'

export default {
    data() {
        return {
          store: store,
          src: 'https://image.tmdb.org/t/p/w185',
          srcFlag: '',
          

        }
    },    
    methods: {
        getFlags() {
             
            if (this.card.original_language === 'en') {
                this.srcFlag = 'https://flagsapi.com/GB/flat/16.png'
            } else if (this.card.original_language === 'it') {
                this.srcFlag = 'https://flagsapi.com/IT/flat/16.png'
            } else if (this.card.original_language === 'fr') {
                this.srcFlag = 'https://flagsapi.com/FR/flat/16.png'
            } else if (this.card.original_language === 'es') {
                this.srcFlag = 'https://flagsapi.com/ES/flat/16.png'
            }else if (this.card.original_language === 'de') {
                this.srcFlag = 'https://flagsapi.com/DE/flat/16.png'
            } else {
                null
            }
        },
        getIntegers(vote) {            
            return (Math.ceil(vote/2))
        }
        
    },
    props: {
        card: Object,
        
    },
    components: {
        
    },
    created() {        
        this.getFlags();             
    },
}

</script>

<template>
    
    <div class="col-3">
        <div class="card">
            <div class="card-header">
                <img :src='src + card.poster_path' alt="">
            
            </div>
            <div class="card-body">

                <p class="title">
                    Titolo: {{ card.title }}
                </p>
                <p class="original-title">
                    Titolo Originale: {{ card.original_title }}
                </p>
                <p class="flag-language language" v-if="srcFlag">
                    <p>Lingua:</p> 
                    <span >                    
                        <img :src="srcFlag" alt="">
                    </span>
                </p>
                <p class="language" v-else>
                    <p>Lingua:</p>
                    {{ card.original_language }}
                </p>
                <p class="vote">
                    <!-- Voto:{{ parseInt(card.vote_average) }} -->
                    Voto: {{ getIntegers(card.vote_average) }}
                    
                </p>
                <div class="star-container">
                    <p v-for="star in getIntegers(card.vote_average)">&star;</p>
                    
                </div>
            </div>
            
        </div>
        
    </div>
    
    
    
</template>

<style lang="scss" scoped>
.card {
    
    background-color: antiquewhite;
    border-radius: 20px;
    padding: 10px;   
    height: 100%; 
}

.col-3 {
    flex-basis: calc((100% / 12) * 3);     
    padding-right: 10px;  
    height: 300px; 

}
.language {
    display: flex;
    gap: 2px;
    align-items: center;
}

.star-container {
    display: flex;
}

.card-body {
    display: none;
}

.card:hover .card-body {
    display: block;
}

.card:hover .card-header {
    display: none;
}

</style>