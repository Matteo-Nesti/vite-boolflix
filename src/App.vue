<template>
  <div>
    <input type="text" v-model="searchTerm" @keyup.enter="onSearchTerm(searchTerm)">
    <button @click="onSearchTerm(searchTerm)">Cerca</button>
    <h2>films</h2>
    <ul>
      <li v-for="film in store.films" :key="film.id">
        Titolo: {{ film.title }} <br>
        Titolo originale: {{ film.original_title }} <br>
        <img :src="getImagePath(film.original_language)" :alt="film.original_language"><br>
        Voto: {{ film.vote_average }}
        <img :src="getThumbimage(film.poster_path)" :alt="film.title">
      </li>
    </ul>
    <h2>series</h2>
    <ul>
      <li v-for="serie in store.series">
        Titolo: {{ serie.name }} <br>
        Titolo originale: {{ serie.original_name }} <br>
        <img :src="getImagePath(serie.original_language)" :alt="serie.original_language"> <br>
        Voto: {{ serie.vote_average }}
      </li>
    </ul>
  </div>
</template>

<script>
const endPointFilms = 'https://api.themoviedb.org/3/search/movie'
const endPointSeries = 'https://api.themoviedb.org/3/search/tv'
const imageThumb = 'https://image.tmdb.org/t/p/'
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
    getThumbimage(url) {
      return imageThumb + 'w342' + url
    },

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
      const filterEndpointFilms = `${endPointFilms}?api_key=${api_key}&query=${this.filteredTerm}&language=it`
      const filterEndpointSeries = `${endPointSeries}?api_key=${api_key}&query=${this.filteredTerm}&language=it`
      this.fetchFilms(filterEndpointFilms)
      this.fetchSeries(filterEndpointSeries)
    },
  }
}
</script>

<style lang="">
  
</style>