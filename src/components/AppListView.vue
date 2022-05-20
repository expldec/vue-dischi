<template>
  <AppLoading v-if="loading" />
  <div v-else class="app-list__container container">
      <AppListFilter @pickedGenre="updateFilter('genre',$event)" @pickedArtist="updateFilter('artist',$event)" :artists="artistArray"/>
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
        artist: '',
      }
    };
  },
  methods: {
    updateFilter(key, filter) {
      this.filter[key] = filter;
    },
  },
  computed: {
    filteredAlbums: function() {
      const filteredAlbums = this.discList.filter((item) => {
        return (item.genre.toLowerCase().includes(this.filter.genre) && item.author.toLowerCase().includes(this.filter.artist));
      });
      return filteredAlbums;
    },
    artistArray: function() {
      const artistArray = this.discList.reduce(       // qui ho voluto usare reduce per creare l'array degli artisti
        (previous, current) => {                      // a ogni giro del reduce, prende il risultato del giro prima
          if (!previous.includes(current.author)) {   // se l'array che stiamo costruendo NON include già l'artista di questo giro
            previous.push(current.author);            //    Pushamo l'artista nell'array
            return previous;                          // passiamo l'array così modificato al prossimo giro del reduce
          }
        }, []                                         // valore del previous nel primo giro (array vuoto)
      );
      return artistArray
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
