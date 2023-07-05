<template>
  <div>
    <input type="text" v-model="searchTerm">
    <button @click="onSearchTerm(searchTerm)">Cerca</button>
    <ul>
      <li v-for="film in store.films" :key="film.id">
        {{ film.title }} <br>
        {{ film.original_title }} <br>
        <img :src="getImagePath(film.original_language)" :alt="film.title"><br>
        {{ film.vote_average }}
      </li>
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
      store,
      searchTerm: '',
      filteredTerm: '',
    }
  },

  computed: {

  },

  methods: {
    getImagePath(lang) {
      if (lang === 'it') {
        return '../src/assets/img/it.png'
      }
      else if (lang === 'en') {
        return '../src/assets/img/en.png'
      }
      else {
        return ''
      }
    },

    fetchFilms(url) {
      axios.get(url).then((res) => {
        store.films = res.data.results
        console.log(store.films)
      })
    },

    onSearchTerm(term) {
      this.filteredTerm = term;
      const filterEndpoint = `${endPointFilms}?api_key=${api_key}&query=${this.filteredTerm}`
      this.fetchFilms(filterEndpoint)
    },
  }
}
</script>

<style lang="">
  
</style>