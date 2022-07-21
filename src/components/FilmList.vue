<template>
  <div class="row justify-content-center">
    <h2>Movies</h2>
     <ul v-for="(item, index) in MovieArray" :key="index" class="col-3 bg-primary mx-2 ">
        <li><img :src="imgUrl + item.poster_path" alt=""></li> 
        <li>
            {{item.title}}
        </li>
        <li>
            {{item.original_title}}
        </li>
        <li>
        <LanguageFlag
            :language = item.original_language
        />
        </li>
        <li>
            {{item.vote_average}}
        </li>
    </ul>
  </div>
</template>

<script>
import LanguageFlag from './LanguageFlag.vue';

export default {
    data() {
        return {
            imgUrl: 'https://image.tmdb.org/t/p/w342/'
        }
    },
    components:{
        LanguageFlag
    },
    props:{
        MovieArray: Array
    },
}
</script>

<style lang='scss'>
li{
    
    img{
        width: 100%;
    }
}
</style>