<template>
  <div>
    <h2>Series</h2>
     <ul v-for="(item, index) in SeriesArray" :key="index" class="col-2 mx-2 bg-primary">
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