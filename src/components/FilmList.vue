<template>
  <div class="row justify-content-center">
    <h2>Movies</h2>
<!--      <ul v-for="(item, id) in MovieArray" :key="id" class="col-3 bg-primary mx-2 ">
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
            <span v-for="n in convertVote(item.vote_average)" :key='n'>⭐</span>
            
        </li>
    </ul> -->

    <div v-for="(item, id) in MovieArray" :key="id"  class="col-3 mx-2 my-2 card-thumb">
        <div class="img-container position-relative"  >
        <img :src="checkImageUrl(item.poster_path)" :alt="item.title"
        class="display-inline-block">
        <div class="card-info position-absolute">
            <ul>
                <li>
                    Title: {{item.title}}
                </li>
                <li>
                    Original Title : {{item.original_title}}
                </li>
                <li>
                    <LanguageFlag
                    :language = item.original_language
                    />  
                </li>
                <li>
                    <span v-for="n in convertVote(item.vote_average)" :key='n'>⭐</span>
                </li>
                <li>
                    <div class="item-overview">
                    {{item.overview}}
                    </div>
                </li>
            </ul>
        </div>
        </div>


    </div>
  </div>
</template>

<script>
import LanguageFlag from './LanguageFlag.vue';

export default {
    data() {
        return {
            imgUrl: 'https://image.tmdb.org/t/p/w342/',
            convertedVote: 0,
            show:false,
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

<style lang="scss" scoped>


.card-thumb{
    .img-container{
        width: 415px;
        height: 600px;
        img{
            width: 100%;
            height: 100%;
        }
    }
        &:hover .card-info{
            visibility: visible;
        }
    .card-info{
        bottom: 0;
        right:0%;
        background-color: grey;
        width: 415px;
        max-height: 300px;
        padding: 1rem;
        overflow: hidden;
        visibility: hidden;
        .item-overview{
            max-height: 100px;
            overflow: hidden;
        }
        ul{
            display: flex;
            flex-direction: column;
        }

    }

}
    


</style>