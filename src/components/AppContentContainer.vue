<script>
import AppSearch from './AppSearch.vue';
import axios from 'axios';
import { store } from '../store.js';
import FilmCard from './FilmCard.vue';
export default{
    name: 'AppContentContainer',
    components:{
        AppSearch,
        FilmCard
    },
    data(){
        return{
            
            store,
        }
    },
    methods: {
        getFilm(){
            console.log('ho preso i film dalla api');
            const QParams = {
                api_key: 'de66ddafc47e3ea64eb8f30eb0014631',
                
            };
            if(store.searchedContent !== ''){
                QParams.query = store.searchedContent;
            }
            
            
            
            axios.get('https://api.themoviedb.org/3/search/movie',{
                params: QParams
                
            })
        .then((response) => {
            this.store.filmArray = response.data.results;
            console.log(store.filmArray)
            
        })
        
        console.log(QParams)


            }
    }

}
</script>

<template>
   <AppSearch @searchPerformed="getFilm"></AppSearch>
   <FilmCard :filmInfo="film" v-for="film in store.filmArray" :key="film.id"></FilmCard>
</template>

<style scoped lang="scss"></style>