<template>
  <AppLoading v-if="loading" />
  <div v-else class="app-list__container container">
    <div class="row row-cols-1">
      <AppListFilter @pickedGenre="genreFilter($event)" />
    </div>
    <div class="row row-cols-2 row-cols-md-4 g-2">
      <AppAlbumCard v-for="(item, index) in filteredAlbums" :key="index" :album="item" />
    </div>
  </div>
</template>

<script>
import AppAlbumCard from "./AppAlbumCard.vue";
import AppLoading from "./AppLoading.vue";
import AppListFilter from "./AppListFilter.vue";
import axios from "axios";

export default {
  name: "AppListView",
  components: {
    AppAlbumCard,
    AppLoading,
    AppListFilter,
  },
  data() {
    return {
      discList: [],
      loading: true,
      filter: {
        genre: '',
      }
    };
  },
  methods: {
    genreFilter(genre) {
      this.filter.genre = genre;
    },
  },
  computed: {
    filteredAlbums: function() {
      const genreFormatted = this.filter.genre.toLowerCase();
      const filteredAlbums = this.discList.filter((item) => {
        return item.genre.toLowerCase().includes(genreFormatted);
      });
      return filteredAlbums;
    },
  },
  created() {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((resp) => {
      this.discList = resp.data.response;
      setTimeout(() => {
        this.loading = false;
      }, 500);
    });
  },
};
</script>

<style lang="scss" scoped>
.app-list__container {
  padding-top: 2rem;
  color: white;
}
</style>
