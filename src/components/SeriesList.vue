<template>
  <div class="row justify-content-center">
    <h2>Series</h2>
     <ul v-for="(item, index) in SeriesArray" :key="index" class="col-2 bg-primary mx-2">
        <li>
            <img :src="checkImageUrl(item.poster_path)" class="mt-1" :alt="item.title"></li> 
        <li>
        <li>
            {{item.name}}
        </li>
        <li>
            {{item.original_name}}
        </li>
        <li>
        <LanguageFlag
            :language = item.original_language
        />
        </li>
        <li>
           <span v-for="n in convertVote(item.vote_average)" :key='n'>⭐</span>
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
        SeriesArray: Array
    },
    methods: {
        checkImageUrl(url){
            if(url == null || url === '') 
            return 'https://i.pinimg.com/474x/e1/30/1a/e1301a5564175ad4c073fd2e6d13617c.jpg'
            else{
                return this.imgUrl + url
            }
            
        },
        convertVote(vote){
            return Math.max(Math.ceil(vote / 2), 1)
        },

    },
}
</script>

<style lang='scss'>

</style>