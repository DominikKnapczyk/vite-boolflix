<script>
import SearchBar from './components/SearchBar.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';
import { store } from './data/store';


export default {
  data() {
    return {
      appname:"BOOLFLIX",
      baseUrl: "https://api.themoviedb.org/3",
      apiKey: "1757eb1da7323401a81905ceca80ad38",
    };
  },

  components: { SearchBar, AppMain },

  methods: {
    fetchMovies(query) {
      axios
        .get(`${this.baseUrl}/search/movie`, {
          params: {
            api_key: this.apiKey,
            query,
          },
        })
        .then((response) => {
          store.filmList = response.data.results;
        });
    }
  },
};
</script>

<template>
  <SearchBar :title="appname" @performSearch="fetchMovies"></SearchBar>
  <div class="container">
    <AppMain></AppMain>
  </div>
</template>

<style lang="scss"></style>