<template>
  <div id="app">
    <Header @findGenre="getGenre" />
    <Main :cditem="cdList" />
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
        })
        .catch((err) => console.log(err));
    },
    getGenre(selection) {
      console.log(selection);
    },
  },
};
</script>

<style lang="scss">
@import "@/styles/global";
</style>
