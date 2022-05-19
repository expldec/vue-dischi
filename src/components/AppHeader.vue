<template>
  <header class="p-3">
    <div class="header__logo rounded-circle">
      <img src="../assets/discogs-record-icon.svg" alt="" />
    </div>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";
@import "../style/common.scss";
header {
  min-height: 4rem;
  background-color: $background-secondary;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  
  .header__logo {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: white;
    height: 3rem;
    width: 3rem;
  }
  img {
    height: 90%;
  }
}
</style>
