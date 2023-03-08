<script>
export default {
  props: {
    title: String,
    originalTitle: String,
    lang: String,
    vote: Number,
  },

  methods: {
    getFlag(country) {
      country = country.toUpperCase();

      if (country == "EN") return "https://flagsapi.com/GB/flat/64.png"
      return "https://flagsapi.com/" + country + "/flat/64.png";
    },
  },
};


</script>

<template>
    <ul class="col">
      <li>title: {{ title }} </li>
      <li>original_title: {{ originalTitle }}</li>
      <li>
        <img :src="getFlag(lang)">
      </li>
      <li>vote_average: {{ vote }} </li>
    </ul>
</template>

<style lang="scss" scoped></style>