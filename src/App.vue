<template>
  <div id="app">
    <Header @searchInput='searchCallBack' />
    <Main 
    :MovieArray = 'movieResultArray'
    :SeriesArray = 'seriesResultArray'
    :apiKey = 'apiKey'
    />
    
  </div>
</template>

<script>
import axios from 'axios'
import Header from './components/Header.vue'
import Main from './components/Main.vue'


export default {
  name: 'App',
  components: {
    Header,
    Main,

  },
  data() {
    return {
      searchQuery:'',

      apiSearch: 'https://api.themoviedb.org/3/search/',
      apiMovie:'movie?',
      apiSeries:'tv?',
      apiKey:'api_key=fc7176f21c9d0e2ebc73ae83e20968a4',
      addQuery:'&query=',
      userQuery:'ritorno',
      movieResultArray:[],
      seriesResultArray:[],


    }
  },
  methods: {
     getMovies(){
      axios.get(
          this.apiSearch+
          this.apiMovie+
          this.apiKey+
          this.addQuery+
          this.searchQuery
          )
          .then((response) =>{
              this.movieResultArray = response.data.results;
              console.log(this.movieResultArray)
          })
          .catch((error) =>{
              console.warn(error)
          })
      },
      getSeries(){
      axios.get(
          this.apiSearch+
          this.apiSeries+
          this.apiKey+
          this.addQuery+
          this.searchQuery
          )
          .then((response) =>{
              this.seriesResultArray = response.data.results;
              console.log(this.seriesResultArray)
          })
          .catch((error) =>{
              console.warn(error)
          })
      },
    searchCallBack(input){
      this.searchQuery = input
      this.getMovies()
      this.getSeries()
    }
  },
    mounted() {
   
  },


}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  background-color: #141414;

  ul{
    list-style: none;
    padding: 0;
    margin: 0;
  }
}
</style>
