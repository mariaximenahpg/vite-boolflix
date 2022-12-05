<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
import { store } from "./store";
import axios from "axios";
export default {
  components: {
    AppHeader,
    AppMain
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    getDataResults() {
      axios
      .get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "eba74913298e0a7ebe4f0a3280afc6de",
          query: this.store.searchText,
          language: "it-IT",
        },
      })
      .then((resp) => {
       this.store.movies = resp.data.results;
      });
      axios
      .get("https://api.themoviedb.org/3/search/tv", {
        params: {
          api_key: "eba74913298e0a7ebe4f0a3280afc6de",
          query: this.store.searchText,
          language: "it-IT",
        },
      })
      .then((resp) => {
       this.store.series = resp.data.results;
      });
    },
  }, 
};
</script>

<template>
  <div class="app-container">
    <AppHeader  @search="getDataResults"/>
    <AppMain />
  </div>
</template>

<style lang="scss">
@import './style/global.scss';
</style>