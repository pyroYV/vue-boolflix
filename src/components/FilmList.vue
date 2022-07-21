<template>
  <div class="row justify-content-center">
    <h2>Movies</h2>
     <ul v-for="(item, index) in MovieArray" :key="index" class="col-2 bg-primary mx-2">
        <li>
            {{item.title}}
        </li>
        <li>
            {{item.original_title}}
        </li>
        <li>
            {{item.original_language}}
        </li>
        <li>
            {{item.vote_average}}
        </li>
    </ul>
  </div>
</template>

<script>
export default {
    data() {
        return {
            
        }
    },
    props:{
        MovieArray: Array
    },
}
</script>

<style lang='scss'>

</style>