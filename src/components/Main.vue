<template>
  <section class="main">
    <div class="container">
      <ul class="container-cd-list">
        <li>
          <div class="card-cd">
            <div class="cover-cd">
              <img
                src="https://m.media-amazon.com/images/I/71K9CbNZPsL._SS500_.jpg"
                alt="titolo cd"
              />
            </div>
            <div class="info-cd text-center mt-3">
              <div class="title-cd mb-2 text-uppercase">Bad</div>
              <div class="author mb-1">Michael Jackson</div>
              <div class="year mb-1">1987</div>
              <div class="genre mb-1">Pop</div>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  name: "Main",
  data() {
    return {
      cdList: [],
    };
  },
  created() {
    this.getCdList();
  },
  computed: {
    dataOk() {
      return this.cdList.length === 10 ? true : false;
    },
  },
  methods: {
    getCdList() {
      // Get cd list from API
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((result) => {
          this.cdList.push(result.data.response);
          console.log(this.cdList);
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/main";
</style>
