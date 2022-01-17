<template>
  <div id="myModal" class="modal">
    <!-- Modal content -->
    <div class="modal-content">
      <span class="close" role="button" @click="closeModal">&times;</span>
      <div class="modal-inner">
        <img :src="selectedImage.urls.regular" class="modal-image" alt="" />
        <div class="selected-image-info">
          <h3 class="author-name">
            <span>{{ selectedImage.user.first_name }} </span>
            <span>{{ selectedImage.user.last_name }}</span>
          </h3>
          <p class="location">{{ selectedImage.user.location }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    imageSrc: {
      type: String,
    },
    selectedImage: {
      type: Object,
    },
  },
  methods: {
    closeModal() {
      this.$emit("toggle-modal");
    },
  },
};
</script>


<style lang="scss" scoped>
.modal {
  display: block; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  /* overflow: auto;  */
  /* Enable scroll if needed */
  background-color: rgb(0, 0, 0); /* Fallback color */
  background-color: rgba(0, 0, 0, 0.4); /* Black w/ opacity */

  .modal-content {
    background-color: #fefefe;
    margin: 8% auto; /* 15% from the top and centered */
    padding: 0px;
    border: 1px solid #888;
    border-radius: 10px;
    width: 60%; /* Could be more or less, depending on screen size */
    position: relative;

    img {
      width: 100%;
      height: 500px;
      object-fit: cover;
      border-radius: 10px 10px 0 0;
      object-position: 10% 33%;
    }

    .selected-image-info {
      padding: 30px 50px;
    }

    .close {
      color: #fff;
      position: absolute;
      /* float: right; */
      font-size: 28px;
      font-weight: bold;
      right: -30px;
      top: -30px;

      &:hover,
      &:focus {
        color: #fff;
        text-decoration: none;
        cursor: pointer;
      }
    }
  }
}

</style>