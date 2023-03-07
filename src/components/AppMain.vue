<script>
export default {
  props: {
    filmList: Array,
  }
};
</script>

<template>
  <h2>Films</h2>
  <ul v-for="film in filmList">
    <li>
      {{ film.title  }}
    </li>
    <li>
      {{ film.original_title  }}
    </li>
    <li>
      {{ film.original_language  }}
    </li>
    <li>
      {{ film.vote_average  }}
    </li>
  </ul>
</template>

<style lang="scss" scoped></style>