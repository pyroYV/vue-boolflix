<template>
  <div class="row justify-content-center">
    <h2>Series</h2>
     <ul v-for="(item, index) in SeriesArray" :key="index" class="col-2 bg-primary mx-2">
        <li>
            {{item.name}}
        </li>
        <li>
            {{item.original_name}}
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
        SeriesArray: Array
    },
}
</script>

<style lang='scss'>

</style>