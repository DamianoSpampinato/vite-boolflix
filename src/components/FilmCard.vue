<script>

export default{
    name :'FilmCard.vue',
    props:{
        filmInfo: Object
    },
    data(){
        return{
            flagArray : ['it', 'en']

            
        }
        
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
    <div v-if="flagArray.includes(filmInfo.original_language)">
        <div class="img-container">
            <img :src="getImageUrl(filmInfo.original_language)" :alt="`language: ${filmInfo.original_language}`">
        </div>
        
    </div>
     
    <div v-else>
        LINGUA: {{ filmInfo.original_language }}
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