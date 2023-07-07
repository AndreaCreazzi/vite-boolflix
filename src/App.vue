<script>
// axios
import axios from 'axios';
// store
import { store } from './data/store'
// AppHeader
import AppHeader from './components/AppHeader.vue';
// AppMain
import AppMain from './components/AppMain.vue';
// api
import { api } from './data';
export default {
  // Components Vue
  components: { AppHeader, AppMain },
  data() {
    return {
      store,
      nameFilter: ""
    }
  },
  methods: {
    // function for getting movies url
    fetchFilms(url) {
      axios.get(url).then(res => {
        this.store.film = res.data.results
      })
    },
    // function for getting series url
    fetchTv(url) {
      axios.get(url).then(res => {
        this.store.tv = res.data.results
      })
    },
    // function for filter term
    onTermChange(term) {
      this.nameFilter = term
    },
    // function for filter in searchbar
    searchItem() {
      const filteredFilm = `${api.endpoint}${api.movie}${api.api_key}&query=${this.nameFilter}`
      const filteredtv = `${api.endpoint}${api.tv}${api.api_key}&query=${this.nameFilter}`
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
