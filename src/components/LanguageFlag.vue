<template>
<span>
{{getFlagEmoji()}}
</span>
</template>

<script>
export default {
    props:{
        language: String
    },
    methods: {
        getFlagEmoji() {
        
            const codePoints = this.flagSpecialCases(this.language)
                .toUpperCase()
                .split('')
                .map(char =>  127397 + char.charCodeAt());
            return String.fromCodePoint(...codePoints);
        },
        flagSpecialCases(input){
            switch(input){
                case 'en' : 
                    return 'gb'
                case 'ja':
                    return 'jp'
                case 'ko':
                    return 'kr'
                case 'fa':
                    return 'ir'
                case 'zh':
                    return 'cn'
                case 'da':
                    return 'dk'
            } 
            
            return input
        }
    },

}
</script>

<style>

</style>