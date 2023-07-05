<script>
import axios from 'axios';
import { store } from './data/store'
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
const endpoint = 'https://api.themoviedb.org/3/search/'
const searchTv = {
  tv: 'tv?',
  api_key: 'api_key=32a657d19bc99fae056014a936cdb307'
}
export default {
  components: { AppHeader, AppMain },
  data() {
    return {}
  },
  methods: {
    fetchBoolflix(url) {
      axios.get(url).then(res => {
        store.item = res.data.result
      })
    }
  },
  created() {
    this.fetchBoolflix(endpoint)
  }
}
</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style></style>
