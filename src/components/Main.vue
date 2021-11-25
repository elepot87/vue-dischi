<template>
  <section class="main">
    <div class="container">
      <ul
        class="container-cd-list d-flex flex-wrap justify-content-center"
        v-if="dataOk"
      >
        <li v-for="cd in cdList" :key="cd" class="mb-3">
          <Card
            :image="cd.poster"
            :title="cd.title"
            :subtitle="cd.author"
            :info1="cd.year"
            :info2="cd.genre"
          />

          <!-- <div class="card-cd">
            <div class="cover-cd">
              <img :src="cd.poster" :alt="cd.title" />
            </div>
            <div class="info-cd text-center mt-3">
              <div class="title-cd mb-2 text-uppercase">
                {{ cd.title }}
              </div>
              <div class="author mb-1">{{ cd.author }}</div>
              <div class="year mb-1">{{ cd.year }}</div>
              <div class="genre mb-1">{{ cd.genre }}</div>
            </div>
          </div> -->
        </li>
      </ul>
      <Loader v-else />
    </div>
  </section>
</template>

<script>
import axios from "axios";
import Card from "@/components/Card.vue";
import Loader from "@/components/Loader.vue";

export default {
  name: "Main",
  components: {
    Card,
    Loader,
  },
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
          this.cdList = result.data.response;
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
