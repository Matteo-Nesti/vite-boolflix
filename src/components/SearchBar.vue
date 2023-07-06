<template lang="">
    <input type="text" 
    v-model="searchTerm" 
    @keyup="$emit('term-change', searchTerm)">
    <button @click="$emit('submit')">Cerca</button>
</template>

<script>
export default {
    emits: ['term-change', 'submit'],
    data() {
        return {
            searchTerm: ''
        }
    },

}
</script>

<style lang="">
    
</style>