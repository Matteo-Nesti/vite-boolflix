<template>
  <div>
    <AppHeader @term-change="onSearchTerm" @submit-button="onSubmit" />
    <!-- <input type="text" v-model="searchTerm" @keyup.enter="onSearchTerm(searchTerm)">
    <button @click="onSearchTerm(searchTerm)">Cerca</button> -->
    <AppMain />
    <!-- <h2>films</h2>

    <ul v-for="film in store.films" :key="film.id">
      <li> {{ film.title }} </li>
      <li> {{ film.original_title }} </li>
      <li>
        <img :src="getImagePath(film.original_language)" :alt="film.original_language">
      </li>
      <li>
        <img :src="getThumbimage(film.poster_path)" :alt="film.title">
      </li>
      <li> {{ film.vote_average }} </li>
    </ul>

    <h2>series</h2>
    <ul v-for="serie in store.series" :key="serie.id">
      <li>{{ serie.name }}</li>
      <li>{{ serie.original_name }}</li>
      <li>
        <img :src="getImagePath(serie.original_language)" :alt="serie.original_language">
      </li>
      <li>{{ serie.vote_average }}</li>
    </ul> -->
  </div>
</template>

<script>
const endPointFilms = 'https://api.themoviedb.org/3/search/movie'
const endPointSeries = 'https://api.themoviedb.org/3/search/tv'
const imageThumb = 'https://image.tmdb.org/t/p/'
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