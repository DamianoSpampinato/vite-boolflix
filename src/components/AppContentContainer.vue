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
   <div class="container">
       <h1 v-show="store.filmArray.length > 0">Film</h1>
       <div class="content-list">
           <FilmCard :filmInfo="film" v-for="film in store.filmArray" :key="film.id"></FilmCard>
        </div>
        <h1 v-show="store.tvSeriesArray.length > 0">Serie Tv</h1>
        <div class="content-list">
            <FilmCard :filmInfo="series" v-for="series in store.tvSeriesArray" :key="series.id"></FilmCard>
        </div>
    </div>
</template>

<style scoped lang="scss">
.container{
    width:  1400px;
    margin: 0 auto;
}

h1{
    color: red;
}
.content-list{
    display: flex;
    overflow-y: clip;
    overflow-x: auto;
    width: 100%;
}
::-webkit-scrollbar {
    height: 10px;
    background-color: black;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    transition: ease-in-out;
  }
::-webkit-scrollbar:hover{
    height: 15px;
}

  ::-webkit-scrollbar-thumb {
    background-image: radial-gradient(rgba(255, 0, 0, 0.822) 40%, black );
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
}
</style>