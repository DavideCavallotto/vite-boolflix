<script>
import { store } from '../store'

export default {
    props: {
        card: Object,

    },
    data() {
        return {
            store: store,
            src: 'https://image.tmdb.org/t/p/w185',
            srcFlag: '',
            srcNone: 'https://image.tmdb.org/t/p/w185null',
            flagsMap: {
                en: 'https://flagsapi.com/GB/flat/16.png',
                it: 'https://flagsapi.com/IT/flat/16.png',
                fr: 'https://flagsapi.com/FR/flat/16.png',
                es: 'https://flagsapi.com/ES/flat/16.png',
                de: 'https://flagsapi.com/DE/flat/16.png'
            }
        }
    },
    methods: {
        getFlags() {
            this.srcFlag = this.flagsMap[this.card.original_language];
        },
    },
    computed: {
        vote() {
            return Math.ceil(this.card.vote_average / 2)
        }
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

                <div class="red" v-if="card.title">
                    <p>Titolo:</p>
                    <p class="white">{{ card.title }}</p>
                </div>
                <div class="red" v-else>
                    <p>Titolo:</p>
                    <p class="white">{{ card.name }}</p>
                </div>
                <p></p>
                <div class="red" v-if="card.original_title">
                    <p>Titolo Originale:</p>
                    <p class="white">{{ card.original_title }} </p>
                </div>
                <div class="red" v-else>
                    <p>Titolo Originale:</p>
                    <p class="white">{{ card.original_name }}</p>
                </div>
                <div class="flag-language language red" v-if="srcFlag">
                    <p>Lingua:</p>
                    <img :src="srcFlag" alt="">

                </div>
                <div class="language red" v-else>
                    <p>Lingua:</p>
                    <p class="white">{{ card.original_language }}</p>
                </div>
                <div class="vote red">
                    <!-- Voto:{{ parseInt(card.vote_average) }} -->
                    <p>Voto:</p>
                    <p class="white">{{ vote }}</p>
                </div>
                <div class="star-container">
                    <p v-for="star in vote" class="star-vote">&starf;</p>
                    <p v-for="star in 5 - vote">&star;</p>

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

    .card-header {
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
            margin-right: 5px;
        }

        .red {
            color: crimson;

            .white {
                color: white;
            }
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
    font-size: 24px;

    .star-vote {
        color: gold;
    }

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