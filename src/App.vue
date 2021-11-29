<template>
  <div id="app">
    <Header @findGenre="getGenre" :genreList="genreList" />
    <Main :cditem="filteredGenres" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      cdList: [],
      selectedGenre: "",
      genreList: [],
    };
  },
  created() {
    this.getCdList();
  },
  methods: {
    getCdList() {
      // Get cd list from API
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((result) => {
          this.cdList = result.data.response;
          console.log(this.cdList);
          this.cdList.forEach((element) => {
            if (this.genreList.includes(element.genre) == false) {
              this.genreList.push(element.genre);
            }
          });
        })
        .catch((err) => console.log(err));
    },
    getGenre(selection) {
      // console.log(selection);
      this.selectedGenre = selection;
    },
  },
  computed: {
    filteredGenres() {
      return this.cdList.filter((item) => {
        return item.genre
          .toLowerCase()
          .includes(this.selectedGenre.toLowerCase());
      });
    },
  },
};
</script>

<style lang="scss">
@import "@/styles/global";
</style>
