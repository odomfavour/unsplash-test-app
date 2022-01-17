<template>
  <header>
    <div class="input-wrapper">
      <input
        type="text"
        placeholder="Search for photo"
        @keyup="handleSearch()"
        v-model="searchQuery"
      />
      <i class="fas fa-search"></i>
      <p class="search-note" v-if="searchQuery">
        Search Results for "{{ searchQuery }}"
      </p>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
      searchPhotos: [],
      uri: "https://api.unsplash.com/photos/?client_id=",
    };
  },
  methods: {
    handleSearch() {
      this.$emit("handleSearch", this.searchQuery);
    },
  },
};
</script>

<style lang="scss" scoped>
header {
  background-color: #dde2e9;
  height: 15rem;
  /* width: 100%; */
  margin: 0 auto;

  .input-wrapper {
    width: 70%;
    margin: 0 auto;
    position: relative;

    input {
      width: 100%;
      margin-top: 50px;
      font-size: 16px;
      padding: 1.2rem 4rem;
      font-size: 1rem;
      border-radius: 0.3rem;
      outline: none;
      border: none;
    }

    i {
      color: gray;
      position: absolute;
      top: 70px;
      left: 32px;
    }

    .search-note {
      margin-top: 30px;
      font-size: 30px;
    }
  }
}
</style>