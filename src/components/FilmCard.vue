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
               
            }
        ]
    }
    

}
</script>
<template>
<div class="card">
    <h5>{{ filmInfo.title }}</h5>
    <small>{{ filmInfo.original_title }}</small>
    <div class="img-container">
        <img :src="`/src/assets/img/${filmInfo.original_language}.png`" :alt="filmInfo.original_language">
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