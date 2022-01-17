<template>
  <div>
    <div v-if="loading">
      <Loader />
    </div>
    <div class="gallery" v-else>
      <!-- {{searchedPhotos}} -->
      <div
        class="card"
        v-for="(photo, index) in searchedPhotos"
        :key="index"
        @click="showImage(photo)"
      >
        <img :src="photo.urls.regular" :alt="photo.alt_description" />
        <div class="image-info">
          <h5 class="author-name">
            <span>{{ photo.user.first_name }} </span>
            <span>{{ photo.user.last_name }}</span>
          </h5>
          <p class="location">{{ photo.user.location }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Loader from "./Loader.vue";
export default {
  components: { Loader },
  props: {
    searchedPhotos: Array,
    loading: Boolean,
  },
  data() {
    return {
      photos: [],
      uri: "https://api.unsplash.com/photos/?client_id=",
    };
  },
  methods: {
    showImage(photo) {
      this.$emit("showImage", photo);
    },
  },
};
</script>

<style lang="scss" scoped>
.gallery {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  width: 70%;
  grid-gap: 30px;
  /* grid-auto-rows: 20px; */
  margin: -60px auto 0 auto;

  .card {
    height: 400px;
    background: chocolate;
    object-fit: cover;
    border-radius: 8px;
    cursor: pointer;
    position: relative;

    &:nth-child(odd),
    &:nth-child(odd) img {
      height: 300px;
      object-fit: cover;
    }

    &:nth-child(4),
    &:nth-child(6),
    &:nth-child(10) {
      margin-top: -90px;
    }

    img {
      width: 100%;
      height: 400px;
      background: #ccc;
      object-fit: cover;
      border-radius: 8px;
      cursor: pointer;
    }
    .image-info {
      margin-top: -80px;
      color: #fff;
      background: linear-gradient(#000000c9, #000000c7);
      height: 80px;
      width: 100%;
      position: absolute;
      padding: 20px;
      border-radius: 0 0 8px 8px;
    }
  }
}

</style>