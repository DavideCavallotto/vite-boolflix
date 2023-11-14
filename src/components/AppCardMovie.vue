<script>
import { store } from '../store'

export default {
    data() {
        return {
          store: store,
          src: 'https://image.tmdb.org/t/p/w185',
          srcFlag: '',
          srcNone: 'https://image.tmdb.org/t/p/w185null'
          

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
    <div class="col-2">
        <div class="card">
            <div class="card-header">
                <div v-if="card.poster_path">
                    <img :src='src + card.poster_path' alt="">               

                </div>
                <div class="poster-none" v-else-if="srcNone">                
                    {{ card.title }}
                    {{ card.name }}
                    <img class="no-img" src="/no-img.png" alt="">
                </div>
                
                
            </div>
            <div class="card-body">

                <p class="title">
                    Titolo: {{ card.title }}
                    {{ card.name }}
                </p>
                <p class="original-title">
                    Titolo Originale: {{ card.original_title }}
                    Titolo Originale: {{ card.original_name }}
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
                <p>
                    {{ card.overview }}
                </p>

            </div>
            
        </div>
        
    </div>    
    
</template>

<style lang="scss" scoped>
.card {
    
    background-color: rgb(0, 0, 0);  
    width: 170px;
    height: 255.45px;    
    
    .card-header{
        .poster-none {
            padding-top: 10px;
            color: white;
            text-align: center;
        }
        
    }
    
    
    .card-body {
        display: none;
        padding: 10px;
        color: white;
        width: 170px;
        height: 255.45px;
        overflow: auto;  
        
        
        p {
            margin-bottom: 5px;
        }  
    }    
    
}
.card:hover .card-body {
    display: block;
}

.card:hover .card-header {
    display: none;
}
.col-2 {
    flex-basis: calc((100% / 12) * 2);     
    padding-right: 10px;     
    
}
.language {
    display: flex;
    gap: 2px;
    align-items: center;
}

.star-container {
    display: flex;
    margin-bottom: 5px;

}
.no-img {
    object-fit: contain;     
}

::-webkit-scrollbar {
    width: 5px;
}

::-webkit-scrollbar-track {
    background: #f1f1f1; 
}

::-webkit-scrollbar-thumb {
    background: #888; 
}

::-webkit-scrollbar-thumb:hover {
    background: #555; 
}

</style>