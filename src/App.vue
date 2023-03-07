<script>
import { createApp, ref } from 'vue';
import axios from 'axios';

const app = createApp({
  setup() {
    const searchTerm = ref('');
    const movies = ref([]);

    function searchMovies() {
      axios
        .get(`https://api.themoviedb.org/3/search/movie`, {
          params: {
            api_key: '1757eb1da7323401a81905ceca80ad38',
            query: searchTerm.value
          }
        })
        .then(response => {
          movies.value = response.data.results;
        })
        .catch(error => {
          console.log(error);
        });
    }

    return {
      searchTerm,
      movies,
      searchMovies,
    };
  },
});

app.mount('#app');
</script>

<template>
    <div id="app">
      <header>
        <div class="header-container">
          <h1>BOOLFLIX</h1>
          <div class="search-container">
            <input type="text" placeholder="Cerca..." v-model="searchTerm" class="search-box">
            <button type="submit" class="search-button" @click="searchMovies">Cerca</button>
          </div>
        </div>
      </header>
      <div class="card-container">
        <div v-for="movie in movies" :key="movie.id" class="card">
          <img :src="'https://image.tmdb.org/t/p/w500/' + movie.poster_path" :alt="movie.title + ' Poster'">
          <h2>{{ movie.title }}</h2>
          <p>Titolo originale: {{ movie.original_title }}</p>
          <p class="rating">Voto: {{ movie.vote_average }}</p>
          <p>{{ movie.overview }}</p>
        </div>
      </div>
    </div>
</template>

<style lang="scss" scoped>
header {
  display: flex;
  justify-content: center;
  height: 100px;
  background-color: black;

  .header-container {
    width: 1400px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    h1 {
      color: red;
      font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
      font-size: 44px;
    }

    .search-container {
      display: flex;
      align-items: center;

      .search-box {
        padding: 10px;
        font-size: 16px;
        border: none;
        border-radius: 5px 0 0 5px;
        width: 200px;
      }

      .search-button {
        background-color: #e50914;
        color: white;
        border: none;
        border-radius: 0 5px 5px 0;
        padding: 10px 20px;
        font-size: 16px;
        cursor: pointer;
        transition: background-color 0.3s ease;
      }

      .search-button:hover {
        background-color: #b2070f;
      }
    }
  }
}

.card-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 20px;
}

.card {
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.2);
  margin: 10px;
  padding: 10px;
  width: 300px;
}

.card h2 {
  font-size: 24px;
  margin-bottom: 5px;
}

.card p {
  font-size: 16px;
  line-height: 1.4;
  margin-bottom: 10px;
}

.card .rating {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 10px;
}

.card img {
  border-radius: 5px;
  width: 100%;
}
</style>