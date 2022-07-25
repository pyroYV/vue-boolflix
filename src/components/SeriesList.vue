<template>
    <div class="row justify-content-center category mt-4">
        <h2 class="ms-3">Series</h2>
        <div class="slider">
            <div v-for="(item, id) in SeriesArray" :key="id" class="mx-2 my-2 card-thumb">
                <div class="img-container position-relative">
                    <img :src="checkImageUrl(item.poster_path)" :alt="item.title" class="display-inline-block">
                    <div class="card-info position-absolute">
                        <ul>
                            <li>
                                Title: {{item.name}}
                            </li>
                            <li>
                                Original Title : {{item.original_name}}
                            </li>
                            <li>
                                <LanguageFlag :language=item.original_language />
                            </li>
                            <li>
                                <span v-for="n in convertVote(item.vote_average)" :key='n'>⭐</span>
                            </li>
                            <li>
                                <div class="item-overview">
                                    {{item.overview}}
                                </div>
                            </li>
                            <li>
                                {{item.id}}
                            </li>
                        </ul>
                    </div>
                    <div class="arrow-info position-absolute" @click="getCastSeries(item.id)">
                        <i class="bi bi-chevron-bar-left"></i>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import LanguageFlag from './LanguageFlag.vue';
import axios from 'axios';


export default {
    data() {
        return {
               imgUrl: 'https://image.tmdb.org/t/p/w342/',
               apiLink:'https://api.themoviedb.org/3/tv/',
               credits:'/credits?',
               castArray: []
               
        }
    },
    components:{
        LanguageFlag
    },
    props:{
        SeriesArray: Array,
        apiKey : String
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
        getCastSeries(id){
            axios
            .get(
                this.apiLink
                + id 
                + this.credits
                + this.apiKey)
            .then((result) => {
                this.castArray = result.data.cast
                this.castArray?.splice(5)
                console.log(this.castArray)
            })
            .catch((error) =>{
                console.warn(error)
            })
        }
    },
}
</script>

<style lang='scss' scoped>
@import '../styles/category.scss'; 
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.9.1/font/bootstrap-icons.css");

</style>