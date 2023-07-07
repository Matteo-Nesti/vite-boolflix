<template>
    <header>
        <h1>BoolFlix</h1>
        <SearchBar @term-change="onSearchTerm" @submit-button="onSubmit" />
    </header>
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

<style lang="scss" scoped>
header {
    height: 80px;
    background-color: rgb(68, 68, 68);
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 2rem;
    color: red;
}

h1 {
    cursor: pointer;
}
</style>