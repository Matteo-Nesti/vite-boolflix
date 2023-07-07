<template>
    <form @submit.prevent class="d-flex justify-content-end">
        <input type="text" class="form-control" v-model="searchTerm" @keyup="$emit('term-change', searchTerm)">
        <button class="btn btn-dark" @click="$emit('submit-button')">Cerca</button>
    </form>
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

<style lang="scss" scoped>
input {
    margin: 0 1rem;
}
</style>