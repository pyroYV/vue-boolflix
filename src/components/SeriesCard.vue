<template>
<div class="img-container position-relative">
    <img :src="checkImageUrl(item.poster_path)" :alt="item.title" class="display-inline-block">

    <div class="card-info position-absolute" v-if="!active">
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
    <div class="card-info position-absolute" v-else>
        <ul>
            <li>
                Cast
            </li>
            <li v-for="(cast, index) in castArray" :key="index">
                {{cast.name}} / {{cast.character}}
            </li>
        </ul>
    </div>
    <div class="arrow-info position-absolute" @click="changeActive(),getCastSeries(item.id)">
        <i class="bi bi-chevron-bar-left"></i>
    </div>
</div>
</template>

<script>
import axios from 'axios';
import LanguageFlag from './LanguageFlag.vue';

export default {
    data() {
        return {
            imgUrl: 'https://image.tmdb.org/t/p/w342/',
            apiLink:'https://api.themoviedb.org/3/tv/',
            credits:'/credits?',
            castArray: [],
            active:false,

        }
    },
    components:{
        LanguageFlag,

    },
    props:{
        item: Object,
        apiKey: String
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
        },
        changeActive(){
            this.active = !this.active
            console.log(this.active)
            
        }
    },

}
</script>

<style lang="scss" scoped>
@import '../styles/card.scss'
        
</style>