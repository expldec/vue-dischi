<template>
  <div class="row row-cols-2 row-cols-md-4 g-2">
    <div class="form-group flex-grow-1">
      <select class="form-select d-flex" aria-label="Genre Select" v-model="genreSelect" @change="$emit('pickedGenre', genreSelect)">
          <option selected value>All genres</option>
          <option v-for="(item,index) in genres" :key="index" :value="item.toLowerCase()">{{ item }}</option>
      </select>
    </div>
    <div class="form-group flex-grow-1">
      <select class="form-select d-flex" aria-label="Artist Select" v-model="artistSelect" @change="$emit('pickedArtist', artistSelect)">
          <option selected value>All artists</option>
          <option v-for="(item,index) in artists" :key="index" :value="item.toLowerCase()">{{ item }}</option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
    name: 'AppListFilter',
    data: function() {
        return {
            genreSelect: '',
            artistSelect: '',
        }
    },
    methods: {
    },
    props: {
        artists: Array,
        genres: Array,
    }
}
</script>

<style>

</style>