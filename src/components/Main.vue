<template>
  <section class="main">
    <div class="container">
      <div class="row">
        <div class="col-6 col-md-4 col-lg-3">cd prova</div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  name: "Main",
  data() {
    return {
      cdList: null,
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
          console.log(result.data.response);
          this.cdList = result.data.response;
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/main";
</style>
