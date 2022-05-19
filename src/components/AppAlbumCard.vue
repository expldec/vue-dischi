<template>
  <div class="col">
    <div class="album-card p-2 text-center">
        <img class="img-fluid" :src="album.poster" alt="" />
        <h2 class="album-title fw-bold mt-3">{{ album.title }}</h2>
    
        <p>{{ album.author }}</p>
        <div>{{ album.year }} &centerdot; {{ album.genre }}</div>
    </div>
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
  height: 100%;
  .album-title {
    font-size: 1.2rem;
    text-transform: uppercase;
    &~* {
        color:$text-lowcontrast-color;
        margin-bottom: 0.2rem;
        font-weight: 500;
    }
  }
}
</style>
