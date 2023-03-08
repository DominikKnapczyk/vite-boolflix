<script>
import { store } from "../data/store";
import BaseCard from "./BaseCard.vue";

export default {
  data() {
    return {
      store,
    };
  },

  components: { BaseCard },
};
</script>

<template>
  <div v-if="store.filmList.length">
    <h2>Films</h2>
    <div class="row row-cols-3">
      <BaseCard 
      v-for="film in store.filmList"
         :title="film.title"
        :originalTitle="film.original_title"
        :lang="film.original_language"
        :vote="film.vote_average"
      />
    </div>
  </div>
  <h2 v-else>Inizia la ricerca</h2>
</template>

<style lang="scss" scoped></style>