<template>
    <div class="mt-3 row justify-content-center category">
        <h2 class="ms-3">Movies</h2>
        <div class="slider">
            <div v-for="(item) in MovieArray" :key="item.id" class=" mx-2 my-2 card-thumb">
             <FilmCard
             :item = 'item'
             :apiKey= "apiKey"
             :filmArrayGenres = 'filmArrayGenres'
              />

            </div>

        </div>
    </div>
</template>

<script>
import axios from 'axios';
import FilmCard from './FilmCard.vue'

export default {
    data() {
        return {
            filmArrayGenres:[],
            apiLinkGenreFilms: 'https://api.themoviedb.org/3/genre/movie/list',
        }
    },
    components:{
        FilmCard,
    },
    props:{
        MovieArray: Array,
        apiKey : String
    },
    methods: {
        /* api call to get movie genres and put them into an array */
        getFilmGenres(){
            axios.
            get(`${this.apiLinkGenreFilms}?${this.apiKey}&language=en-US`)
            .then((result) => {
                this.filmArrayGenres = result.data.genres   
            })
            .catch((error) => {
                console.warn(error)
            })
        }
    },
    mounted(){
        this.getFilmGenres()
    },
}
</script>

<style lang="scss" scoped>
@import '../styles/category.scss';
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.9.1/font/bootstrap-icons.css");


</style>