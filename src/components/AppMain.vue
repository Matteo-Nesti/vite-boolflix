<template lang="">
        <h2>Films</h2>
        <ContentCards  v-for="film in store.films" :key="film.id" :item="film" />
        <h2>Series</h2>
        <ContentCards v-for="serie in store.series" :key="serie.id" :item="serie" />
    
</template>

<script>
import ContentCards from './ContentCards.vue';
import { store } from './data/store';
export default {
    components: { ContentCards },
    data() {
        return {
            store
        }
    },
}
</script>

<style lang="">
    
</style>