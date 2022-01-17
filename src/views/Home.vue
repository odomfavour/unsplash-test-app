<template>
  <div class="home">
    <Header @handleSearch="handleSearch" />
    <Card
      :searchedPhotos="searchPhotos"
      :loading="loading"
      @showImage="showImage"
    />
    <Modal
      @toggle-modal="toggleModal"
      :selectedImage="selectedImage"
      v-if="isVisible"
    />
  </div>
</template>

<script>
import Card from "../components/Card.vue";
// @ is an alias to /src
import Header from "../components/Header.vue";
import axios from "axios";
import Modal from "../components/Modal.vue";
export default {
  name: "Home",
  components: {
    Header,
    Card,
    Modal,
  },
  data() {
    return {
      loading: false,
      searchQuery: "",
      searchPhotos: [],
      uri: "https://api.unsplash.com/photos/?client_id=",
      searchUri: "https://api.unsplash.com/search/photos/?client_id=",
      apiKey: process.env.VUE_APP_KEY,
      isVisible: false,
    };
  },
  methods: {
    showImage(photo) {
      this.selectedImage = photo;
      this.isVisible = true;
    },
    toggleModal() {
      this.isVisible = !this.isVisible;
    },
    handleSearch(value) {
      this.loading = true;
      let myUrl = `${this.searchUri}${this.apiKey}&page=1&query=${value}`;
      if (value != "") {
        return axios
          .get(myUrl)
          .then((response) => {
            this.searchPhotos = response.data.results;
            console.log("search", this.searchPhotos);
            this.loading = false;
            // console.log("search", response.data);
          })
          .catch((error) => {
            console.log(error);
          });
      } else {
        return axios
          .get(`${this.uri}${this.apiKey}`)
          .then((response) => {
            this.searchPhotos = response.data;
            this.loading = false;
            console.log(this.searchPhotos);
          })
          .catch((error) => {
            console.log(error);
          });
      }
    },
  },
  async created() {
    // console.log(this.uri)
    this.loading = true;
    return axios
      .get(`${this.uri}${this.apiKey}`)
      .then((response) => {
        this.searchPhotos = response.data;
        this.loading = false;
        // console.log(this.searchPhotos);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
