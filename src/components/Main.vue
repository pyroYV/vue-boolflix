<template>
<div class="container-fluid">
 
    <FilmList 
    :MovieArray = MovieArray
    :apiKey = apiKey
    />
    <SeriesList 
    :SeriesArray = SeriesArray
    :apiKey = apiKey
    />
   
</div>
</template>

<script>
import FilmList from './FilmList.vue'
import SeriesList from './SeriesList.vue'


export default {

    data() {
        return {
           
            
        }
    },
    components:{
        FilmList,
        SeriesList
    },
    props: {
       MovieArray: Array,
       SeriesArray: Array,
       apiKey : String
    },



}
</script>

<style lang="scss">
    .container{
            overflow-x: auto;

    }

</style>

