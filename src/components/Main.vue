<template>
<div class="container">
  <div class="row">
    <ul v-for="(item, index) in MovieArray" :key="index" class="col-2 mx-2 bg-primary">
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
</div>
</template>

<script>


export default {

    data() {
        return {
           
            
        }
    },
    props: {
       MovieArray: Array
    },



}
</script>

<style lang="scss">
    

</style>

