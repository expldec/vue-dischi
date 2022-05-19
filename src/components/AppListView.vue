<template>
  <div class="app-list__container container">
      ciao
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AppListView",
  data() {
      return {
          discList: [],
          }
  },
  created() {
    axios
    .get("https://flynn.boolean.careers/exercises/api/array/music")
    .then((resp) => {
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
