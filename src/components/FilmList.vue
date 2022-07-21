<template>
  <div class="row justify-content-center">
    <h2>Movies</h2>
     <ul v-for="(item, index) in MovieArray" :key="index" class="col-6 bg-primary mx-2 ">
        <li>
            <img :src="checkImageUrl(item.poster_path)" class="mt-1" :alt="item.title"></li> 
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
    methods: {
        checkImageUrl(url){
            if(url == null || url === '') 
            return 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQbz-qjFpeFVXeIE2W6QbRO8XSR-1EGRl41YQVnIHUzqTTbkED_HPHYhrOENzyu3S_vkvY&usqp=CAU'
            else{
                return this.imgUrl + url
            }
            
        }
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