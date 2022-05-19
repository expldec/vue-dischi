<template>
  <AppLoading v-if="loading" />
  <div v-else class="app-list__container container">
    <div class="row row-cols-2 row-cols-md-4 g-2">
      <AppAlbumCard v-for="(item, index) in discList" :key="index" :album="item" />
    </div>
  </div>
</template>

<script>
import AppAlbumCard from "./AppAlbumCard.vue";
import AppLoading from "./AppLoading.vue";
import axios from "axios";

export default {
  name: "AppListView",
  components: {
    AppAlbumCard,
    AppLoading,
  },
  data() {
    return {
      discList: [],
      loading: true,
    };
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
