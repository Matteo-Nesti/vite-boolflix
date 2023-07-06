<template lang="">
  <SearchBar @term-change="onSearchTerm" @submit="onSubmit" />
</template>

<script>
import SearchBar from './SearchBar.vue';
export default {
    emits: ['term-change', 'submit'],
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
            this.$emit('submit')
        }
    },
}
</script>

<style lang="">
    
</style>