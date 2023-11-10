<script>

export default {
  data() {
    return {
        searchText: '',
    }
  }, 
  props: {
    
  },
  methods: {
    
  }
}

</script>

<template>
    <div class="header-section">
        <div class="container">
            <div class="row">
                <div class="nav">
                    <p class="title-site">BoolFlix</p>
                    <div class="search">
                        <input placeholder="Inserisci cosa vuoi vedere" v-model="searchText">
                        <button @click="$emit('search')">Cerca</button>
                        <p class="scritta">{{ searchText }}</p>

                    </div>
                </div>
                
                
            </div>                
            
            
            
        </div>
            
    </div>    

    
</template>

<style lang="scss" scoped>
.container { 
    margin: 0 auto;
    padding: 0;
}
.row {
      
}

.nav {
    background-color: black;
    padding: 10px;    
    display: flex;
    justify-content: space-between;
    align-items: center;

    .title-site {
        color: red;
        font-size: 24px;
    }
    
    .search {
        display: flex;
        gap: 5px;
    }

}

.scritta {
    color: aliceblue;
}



</style>


