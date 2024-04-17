<script>

export default{
    name :'FilmCard.vue',
    props:{
        filmInfo: Object
    },
    

}
</script>
<template>
<div class="card">
    <h5>{{ filmInfo.title }}</h5>
    <small>{{ filmInfo.original_title }}</small>
    <div>{{ filmInfo.original_language }}</div>
    
    <!-- VOTO MEDIO ARROTONDATO -->
    <div>{{ Math.ceil(this.filmInfo.vote_average) }}</div>
</div>
</template>

<style scoped lang="scss">
.card{
    border: 1px solid red;
}
</style>