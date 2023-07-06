<template lang="">
    <input type="text" 
    v-model="searchTerm" 
    @keyup="$emit('term-change', searchTerm)">
    <button @click="$emit('submit-button')">Cerca</button>
</template>

<script>
export default {
    emits: ['term-change', 'submit-button'],
    data() {
        return {
            searchTerm: ''
        }
    },

}
</script>

<style lang="">
    
</style>