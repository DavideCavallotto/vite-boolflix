<script>
import { store } from '../store'
export default {
  data() {
    return {
        store: store,
        
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
                    <img class="logo" src="/boolflix.png" alt="">                    
                    <div class="search">
                        <input type="text" @keyup.enter="$emit('enterSearch')" placeholder="Cosa vuoi vedere oggi?" v-model="store.userTyping">
                        <button @click="$emit('search')">Cerca</button>                       

                    </div>
                </div>
                
                
            </div>                
            
            
            
        </div>
            
    </div>    

    
</template>

<style lang="scss" scoped>

.header-section {
    overflow: hidden;
}
.container { 
    margin: 0 auto;
    padding: 0;
    
    .nav {
        background-color: black;
        padding: 10px;    
        display: flex;
        justify-content: space-between;
        align-items: center;
        border-bottom: 0.4px solid #E92088;
    
        .title-site {
            color: red;
            font-size: 24px;
        }
        
        .search {
            display: flex;
            gap: 5px;

            input[type=text] {

                width: 100%;
                padding: 10px;
                margin: 8px 0;
                box-sizing: border-box;
                border: 2px solid #E92088;
                border-radius: 4px;
            }

            button {
                padding: 10px;
                color: white;
                background-color: #282B69;
                border: 2px solid #E92088;
                border-radius: 4px;
                margin: 8px 0;
                cursor: pointer;
                
            }

        }

        .logo {
            width: 110px;
        }
    
    }
}

</style>


