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

            
        })
        
        },
        getTvSeries(){
            console.log('ho preso i film dalla api');
            const QParams = {
                api_key: 'de66ddafc47e3ea64eb8f30eb0014631',
                
            };
            if(store.searchedContent !== ''){
                QParams.query = store.searchedContent;
            }
            axios.get('https://api.themoviedb.org/3/search/tv',{
                params: QParams
                
            })
        .then((response) => {
            this.store.tvSeriesArray = response.data.results;
            console.log(store.tvSeriesArray)
            
        })
        
        }
    }

}
</script>

<template>
   <AppSearch @searchPerformed="getFilm(), getTvSeries()"></AppSearch>
   <h1>film</h1>
   <div class="content-list">
       <FilmCard :filmInfo="film" v-for="film in store.filmArray" :key="film.id"></FilmCard>
    </div>
    <h1>Serie Tv</h1>
   <div class="content-list">
       <FilmCard :filmInfo="series" v-for="series in store.tvSeriesArray" :key="series.id"></FilmCard>
    </div>
</template>

<style scoped lang="scss">
.content-list{
    display: flex;
    overflow-y: clip;
    overflow-x: auto;
    width: 100%;
}
</style>