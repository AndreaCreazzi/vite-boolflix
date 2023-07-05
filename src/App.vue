<script>
import axios from 'axios';
import { store } from './data/store'
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
const endpoint = 'https://api.themoviedb.org/3/search/'
const movie = "movie?"
const tv = "tv?"
const api_key = "api_key=32a657d19bc99fae056014a936cdb307"
export default {
  components: { AppHeader, AppMain },
  data() {
    return {
      store,
      nameFilter: ""
    }
  },
  methods: {
    fetchFilms(url) {
      axios.get(url).then(res => {
        this.store.film = res.data.results
      })
    },
    fetchTv(url) {
      axios.get(url).then(res => {
        this.store.tv = res.data.results
      })
    },
    onTermChange(term) {
      this.nameFilter = term
    },
    searchItem() {
      const filteredFilm = `${endpoint}${movie}${api_key}&query=${this.nameFilter}`
      const filteredtv = `${endpoint}${tv}${api_key}&query=${this.nameFilter}`
      this.fetchTv(filteredtv)
      this.fetchFilms(filteredFilm)
    }
  },
}
</script>

<template>
  <AppHeader @term-change="onTermChange" @form-submit="searchItem" />
  <AppMain />
</template>

<style></style>
