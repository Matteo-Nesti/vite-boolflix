<template >
    <main>
        <div class="container mt-5">
            <h2 v-if="store.films.length"> Films</h2>
            <div class="row row-cols-lg-4 row-cols-md-2 g-3">
                <ContentCards v-for="film in store.films" :key="film.id" :item="film" />
            </div>
            <h2 v-if="store.series.length" class="mt-5">Series</h2>
            <div class="row row-cols-lg-4 row-cols-md-2">
                <ContentCards v-for="serie in store.series" :key="serie.id" :item="serie" />
            </div>
        </div>
    </main>
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

<style lang="scss" scoped>
main {
    height: calc(100vh - 80px);
    overflow-y: auto;
    background: rgb(0, 0, 0);
    color: #fff;

}
</style>



