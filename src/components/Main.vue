<template>
<div class="container">
  <div class="row">
    <FilmList 
    :MovieArray = MovieArray
    />
    <SeriesList 
    :SeriesArray = SeriesArray
    />
    
   
  </div>
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
       SeriesArray: Array
    },



}
</script>

<style lang="scss">
    

</style>

