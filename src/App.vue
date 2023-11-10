<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default {
  data() {
    return {
      
    }
  },
  methods: {
    getLog() {
      console.log('ho cliccato')
    }
  },

  components: {
    AppHeader,
    AppMain,
 },


 
}
</script>

<template>

  <AppHeader @search="getLog"/>
  <AppMain/>  

</template>

<style lang="scss">
@use './style/general.scss';
</style>
