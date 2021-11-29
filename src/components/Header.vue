<template>
  <div class="header p-2">
    <img src="../assets/logo.png" alt="logo" class="logo" />
    <div class="container-select">
      <select
        name="selection"
        id="select-genre"
        v-model="genres"
        @change="$emit('findGenre', genres)"
      >
        <option value="">All genres</option>
        <option
          v-for="(genre, index) in genreListNew"
          :key="`genreList-${index}`"
          :value="genre"
        >
          {{ genre }}
        </option>
        <!-- <option value="rock">Rock</option>
        <option value="pop">Pop</option>
        <option value="metal">Metal</option>
        <option value="jazz">Jazz</option> -->
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",

  data() {
    return {
      genres: "",
    };
  },
  props: {
    genreListNew: {
      type: Array,
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/header";
</style>
