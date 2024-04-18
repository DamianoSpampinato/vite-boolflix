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
                <button @click="$emit('searchPerformed')">Cercamelo</button>
             
            </div>
        </div>
    </header>
</template>

<style scoped lang="scss">
@use '../style/generic';
header{
    background-color: black;
    .header{
        color: red;
    }
}
.container{
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 60px;
}
</style>