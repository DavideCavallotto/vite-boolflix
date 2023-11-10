<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store'

import axios from 'axios';
export default {
  data() {
    return {
      store: store,
      API_KEY:'9f1a79a8d7d0192e8b749306792e2da8',
          
      
      
    }
  },
  methods: {
    getLog() {
      console.log('ho cliccato')
    },

    fetchMovies() {
      axios.get('https://api.themoviedb.org/3/search/movie',{
        params: {
          api_key: this.API_KEY,
          query: this.store.userTyping
        }
      }).then(res => {        
        console.log(res.data.results)
        const films = res.data.results
        this.store.infoFilms = films
        this.store.send = true
      })
    }
  },

  components: {
    AppHeader,
    AppMain,
 },


 
}
</script>

<template>

  <AppHeader @search="fetchMovies"/>
  <AppMain v-if="store.send === true"/>  

</template>

<style lang="scss">
@use './style/general.scss';
</style>
