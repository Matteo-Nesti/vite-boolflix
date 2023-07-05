<template>
  <div>
    <input type="text" v-model="searchTerm">
    <button @click="onSearchTerm">Cerca</button>
    <ul>
      <li></li>
    </ul>
  </div>
</template>

<script>
const endPointFilms = 'https://api.themoviedb.org/3/search/movie'
const api_key = 'f54a6d440796635ebf443de82f3b42de'
import { store } from './components/data/store.js';
import axios from 'axios';
export default {
  data() {
    return {
      searchTerm: '',
    }
  },


  methods: {
    fetchFilms(url) {
      axios.get(url).then((res) => {
        store.films = res.data.results
      })
    },

    onSearchTerm() {
      const filterEndpoint = `${endPointFilms}?api_key=${api_key}&query=${this.searchTerm}`
      this.fetchFilms(filterEndpoint)
      console.log(store.films)
    },
  }
}
</script>

<style lang="">
  
</style>