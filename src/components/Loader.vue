<template>
  <div class="gallery">
    <div class="card" v-for="(photo, index) in 10" :key="index">
      <div class="image-info">
        <h5 class="author-name"><span> </span> <span></span></h5>
        <p class="location"></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
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
    background: #ccc;
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
      bottom: 10px;
      color: #fff;
      //   background: linear-gradient(#000000c9, #000000c7);
      height: 80px;
      width: 100%;
      position: absolute;
      padding: 20px;
      border-radius: 0 0 8px 8px;

      .author-name {
        background: rgb(179, 172, 172);
        width: 50%;
        height: 20px;
      }

      .location {
        background: rgb(179, 172, 172);
        width: 70%;
        height: 20px;
        margin-top: 10px;
      }
    }
  }
}
</style>