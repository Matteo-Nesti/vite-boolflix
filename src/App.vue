<template>
  <div>
    <AppHeader @term-change="onSearchTerm" @submit-button="onSubmit" />
    <AppMain />
  </div>
</template>

<script>
const endPointFilms = 'https://api.themoviedb.org/3/search/movie'
const endPointSeries = 'https://api.themoviedb.org/3/search/tv'
const api_key = 'f54a6d440796635ebf443de82f3b42de'

import { store } from './components/data/store.js';
import axios from 'axios';
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
export default {
  components: { AppHeader, AppMain },
  data() {
    return {
      store,
      filteredTerm: '',
    }
  },


  methods: {
    fetchFilms(url) {
      axios.get(url).then((res) => {
        store.films = res.data.results
        console.log(store.films)
      })
    },
    fetchSeries(url) {
      axios.get(url).then((res) => {
        store.series = res.data.results
        console.log(store.series)
      })
    },

    onSearchTerm(term) {
      this.filteredTerm = term;
    },

    onSubmit() {
      const filterEndpointFilms = `${endPointFilms}?api_key=${api_key}&query=${this.filteredTerm}&language=it`
      const filterEndpointSeries = `${endPointSeries}?api_key=${api_key}&query=${this.filteredTerm}&language=it`
      this.fetchFilms(filterEndpointFilms)
      this.fetchSeries(filterEndpointSeries)
    }
  }
}
</script>

<style lang="">
  
</style>