<template>
  <div class="album-card text-center p-3">
    <img class="rounded-circle" :src="album.poster" alt="" />
    <h2 class="album-title fw-bold mt-3">{{ album.title }}</h2>

    <p>{{ album.author }}</p>
    <p class="fw-bold">{{ album.year }}</p>
    <p class="fw-bold">{{ album.genre }}</p>
  </div>
</template>

<script>
export default {
  name: "AppAlbumCard",
  props: {
    album: Object,
  },
};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";
@import "../style/common.scss";

.album-card {
  background-color: $background-secondary;
  .album-title {
    font-size: 1.4rem;
    text-transform: uppercase;
  }
  img {
    width: 100%;
  }
}
</style>
