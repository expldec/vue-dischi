<template>
  <div class="form-group flex-grow-1">
    <select class="form-select" aria-label="Genre Select" v-model="genreSelect" @change="$emit('pickedGenre', genreSelect)">
        <option disabled selected value>Select genre</option>
        <option value="rock">Rock</option>
        <option value="pop">Pop</option>
        <option value="jazz">Jazz</option>
        <option value="metal">Metal</option>
    </select>
    </div>
</template>

<script>
export default {
    name: 'AppListFilter',
    data: function() {
        return {
            genreSelect: '',
        }
    },
    methods: {
    }
}
</script>

<style>

</style>