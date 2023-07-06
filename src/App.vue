<script>
import axios from 'axios';
import { store } from './data/store'
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { api } from './data';
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
