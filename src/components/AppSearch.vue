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
    <div>
        <input type="search" v-model="store.searchedContent">
        <button @click="$emit('searchPerformed')">Cercamelo</button>
        <div>{{ store.searchedContent }}</div>
    </div>
</template>

<style scoped lang="scss"></style>