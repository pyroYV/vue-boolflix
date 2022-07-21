<template>
    <input type="text" v-model='searchQuery' @keyup.enter="emitSearch()" placeholder="Ricerca">
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
    
</style>