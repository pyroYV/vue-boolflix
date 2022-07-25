<template>
    <div class="row justify-content-center category mt-4">
        <h2 class="ms-3">Series</h2>
        <div class="slider">
            <div v-for="(item, id) in SeriesArray" :key="id" class="mx-2 my-2 card-thumb" >
                <SeriesCard 
                :item = 'item'
                :apiKey= "apiKey"
                />
            </div>
        </div>
    </div>
</template>

<script>

import SeriesCard from "./SeriesCard.vue";


export default {
    data() {
        return {

               
        }
    },
    components:{
        SeriesCard,
    },
    props:{
        SeriesArray: Array,
        apiKey : String
    },
    methods: {
       
    },
}
</script>

<style lang='scss' scoped>
@import '../styles/category.scss'; 
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.9.1/font/bootstrap-icons.css");

</style>