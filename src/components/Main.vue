<template>
  
</template>

<script>
import axios from 'axios'

export default {

    data() {
        return {
            apiSearch: 'https://api.themoviedb.org/3/search/',
            apiMovie:'movie?',
            apiKey:'api_key=fc7176f21c9d0e2ebc73ae83e20968a4',
            addQuery:'&query=',
            userQuery:'ritorno',
            movieResultArray:[],

            
        }
    },
    methods: {
        getMovies(){
            axios.get(
                this.apiSearch+
                this.apiMovie+
                this.apiKey+
                this.addQuery+
                this.userQuery
                )
                .then((response) =>{
                    this.movieResultArray = response.data.results;
                    console.log(this.movieResultArray)
                })
                .catch((error) =>{
                    console.warn(error)
                })
        }
    },
    mounted() {
        this.getMovies()
    },


}
</script>

<style lang="scss">
    

</style>

