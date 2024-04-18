<script>
import { store } from '../store.js';
export default{
    name: 'AppSearch',
    data(){
        return{
            store
        }
    }
}
</script>

<template>
    <header>
        <div class="container">
            <div class="header">BOOLFLIX</div>
            <div>
                <input type="search" v-model="store.searchedContent">
                <button class="bta" @click="$emit('searchPerformed')">CERCAMELO</button>
             
            </div>
        </div>
    </header>
</template>

<style scoped lang="scss">
@use '../style/generic';
header{
    background-image: linear-gradient(black,black,black,black,black,black,black,black, white);
    .header{
        color: red;
      
            letter-spacing: 7px;
        
    }
}
.container{
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 60px;
    input,.bta{
        color: red;
        border-radius: 5px;
        widows: 120px;
        height: 100%;
        border: 1px solid red;
        background-color: transparent;
        font-weight: bold;
        padding: 5px;
        margin-left:5px ;
        transition: 150ms ease-in-out;
        cursor: pointer;
    }
    input:active, .bta:active{
        transform: scale(1.1);
    }
   
}
</style>