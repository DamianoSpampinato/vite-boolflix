<script>

export default{
    name :'FilmCard.vue',
    props:{
        filmInfo: Object
    },
    data(){
        flagArray: [
            {
                lang: 'it',
                src: '../assets/img/it.png',
            
            },
            {
                lang: 'en',
                src: '../assets/img/en.png',
            
            },
        ]
    
        
    },
    methods: {
        getImageUrl(flag) {
            
            return new URL(`../assets/img/${flag}.png`  , import.meta.url).href;
            
            }
    }
    

}
</script>
<template>
<div class="card">
    <h5>titolo: {{ filmInfo.title }}</h5>
    <small>titolo originale: {{ filmInfo.original_title }}</small>
    <div v-if="getImageUrl(filmInfo.original_language) === `http://localhost:5173/src/components/undefined`">
        LINGUA: {{ filmInfo.original_language }}
    </div>
    <div v-else class="img-container">
        <img :src="getImageUrl(filmInfo.original_language)" :alt="`language: ${filmInfo.original_language}`">
        
    </div>



    <!-- VOTO MEDIO ARROTONDATO -->
    <div>{{ Math.ceil(this.filmInfo.vote_average) }}</div>
</div>
</template>

<style scoped lang="scss">
.card{
    border: 1px solid red;
    .img-container{
        width: 70px;
        height: 70px;
        img{
            width: 100%;
            height: 100%;
        }
    }
}
</style>