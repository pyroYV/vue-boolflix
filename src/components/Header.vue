<template>
<header class="p-4">
    <div class="d-flex justify-content-between">
        <img src="https://www.freepnglogos.com/uploads/netflix-logo-0.png" alt="">
    <input type="text" v-model='searchQuery' @keyup.enter="emitSearch()" placeholder="Ricerca">
    </div>
</header>
</template>

<script>
export default {
    data() {
        return {
                searchQuery : ''
        }
    },
    methods: {
        emitSearch(){
            this.$emit('searchInput', this.searchQuery)
        }
    },
}
</script>
<style lang="scss">
header{
    background-color: #0a0a0a;
    img{
        height: 30px;
    }
}
    
</style>