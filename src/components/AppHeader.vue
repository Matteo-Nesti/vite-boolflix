<template lang="">
  <SearchBar @term-change="onSearchTerm" @submit-button="onSubmit" />
</template>

<script>
import SearchBar from './SearchBar.vue';
export default {
    emits: ['term-change', 'submit-button'],
    components: { SearchBar },
    data() {
        return {

        }
    },
    methods: {
        onSearchTerm(searchTerm) {
            this.$emit('term-change', searchTerm)
        },

        onSubmit() {
            this.$emit('submit-button')
        }
    },
}
</script>

<style lang="">
    
</style>