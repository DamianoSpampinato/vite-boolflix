<script>

export default{
    name :'FilmCard.vue',
    props:{
        filmInfo: Object
    },
    data(){
        return{
            flagArray : ['it', 'en','es']

            
        }
        
    },
    methods: {
        getImageUrl(flag) {
            
            return new URL(`../assets/img/${flag}.png`  , import.meta.url).href;
            
            },
        
    }
    

}
</script>
<template>
<div class="card">
    <h5>titolo: {{ filmInfo.title || filmInfo.name}}</h5>
    <small>titolo originale: {{ filmInfo.original_title || filmInfo.original_name }}</small>
    <div v-if="flagArray.includes(filmInfo.original_language)">
        <div class="img-container">
            <img :src="getImageUrl(filmInfo.original_language)" :alt="`language: ${filmInfo.original_language}`">
        </div>
        
    </div>
     
    <div v-else>
        LINGUA: {{ filmInfo.original_language }}
    </div>
    <div v-show="filmInfo.poster_path" class="thumbnail">
        <img :src="`https://image.tmdb.org/t/p/w342${filmInfo.poster_path}`" alt="">
    </div>
    <div >Voto medio: 
        <i v-if="Math.ceil(filmInfo.vote_average / 2)>=1" class="fa-solid fa-star color-gold"></i>
        <i v-else class="fa-solid fa-star"></i>
        <i v-if="Math.ceil(filmInfo.vote_average / 2)>=2" class="fa-solid fa-star color-gold"></i>
        <i v-else class="fa-solid fa-star"></i>

        <i v-if="Math.ceil(filmInfo.vote_average / 2)>=3" class="fa-solid fa-star color-gold"></i>
        <i v-else class="fa-solid fa-star"></i>
        <i v-if="Math.ceil(filmInfo.vote_average / 2)>=4" class="fa-solid fa-star color-gold"></i>
        <i v-else class="fa-solid fa-star"></i>
        <i v-if="Math.ceil(filmInfo.vote_average / 2)>=5" class="fa-solid fa-star color-gold"></i> 
        <i v-else class="fa-solid fa-star"></i>

        


          

    </div>
        



    <!-- VOTO MEDIO ARROTONDATO -->
   
</div>
</template>

<style scoped lang="scss">
.card{
    display: flex;
    flex-direction: column;
    flex-shrink: 0;
    width: calc(100% / 5);
    border: 1px solid red;
    position: relative;
    height: 500px;
    .img-container{
        width: 70px;
        height: 70px;
        img{
            width: 100%;
            height: 100%;
        }
    }
    .thumbnail{
        position: absolute;
        width: 100%;
        height: 100%;
        transition: 200ms ease-in-out;
        opacity: 100%;
        img{
            width: 100%;
            height: 100%;
        }
    }
    .thumbnail:hover {
        opacity: 25%;
    }
    .color-gold{
        color: gold;
    }
}
</style>