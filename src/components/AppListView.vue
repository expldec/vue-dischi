<template>
  <div class="app-list__container container">
      <div class="row row-cols-2 row-cols-md-4"><AppAlbumCard :album='discList[0]' /></div>
  </div>
</template>

<script>
import AppAlbumCard from "./AppAlbumCard.vue";
import axios from "axios";

export default {
  name: "AppListView",
  components: {
    AppAlbumCard,
  },
  data() {
    return {
      discList: [],
    };
  },
  created() {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((resp) => {
      this.discList = resp.data.response;
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
