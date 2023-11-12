<script>
import { store } from '../store'

export default {
    data() {
        return {
          store: store,
          src: 'https://image.tmdb.org/t/p/w185',
          srcFlag: ''
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
        }
        
    },
    props: {
        card: Object
    },
    components: {
        
    },
    created() {
        this.getFlags();
    }
}

</script>

<template>
    
    <div class="col-3">
        <div class="card">
            <img :src='src + card.poster_path' alt="">
            <p class="title">
                Titolo: {{ card.name }}
            </p>
            <p class="original-title">
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
                Voto: {{ card.vote_average }}
            </p>
    
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
    height: 450px; 
    padding-right: 10px;   

}
.language {
    display: flex;
    gap: 2px;
    align-items: center;
}
    

</style>