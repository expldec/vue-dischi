<template>
  <div id="app">
    <AppHeader />
    <main>
      <AppListView />
    </main>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppListView from "./components/AppListView.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    AppListView,
  },
};
</script>

<style lang="scss">
@import "./style/variables.scss";
@import "./style/common.scss";
#app {
  height: 100vh;
}
main {
  background-color: $background-primary;
  display: flex;
  flex-direction: column;
  height: calc(100% - 4rem);
}
</style>
