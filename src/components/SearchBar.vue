<script>
export default {
  data() {
    return {
      term: "",
    }
  },

  props: {
    title: String,
  },

  emits: ['performSearch'],
};
</script>

<template>
      <header>
        <div class="header-container">
          <h1>{{ title }}</h1>
          <div class="search-container">
            <input type="text" placeholder="Cerca..." class="search-box" v-model="term" @keyup.enter="$emit('performSearch', term)">
            <button type="submit" class="search-button" @click="$emit('performSearch', term)">Cerca</button>
          </div>
        </div>
      </header>
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
</style>