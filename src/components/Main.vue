<template>
  <section class="main">
    <div class="container">
      <ul class="container-cd-list d-flex flex-wrap justify-content-center">
        <li v-for="(cd, index) in cditem" :key="`cd-${index}`" class="mb-3">
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
      <!-- <Loader /> -->
    </div>
  </section>
</template>

<script>
import Card from "@/components/Card.vue";
// import Loader from "@/components/Loader.vue";

export default {
  name: "Main",
  components: {
    Card,
    // Loader,
  },
  // data() {
  //   return {
  //     cdList: [],
  //     selectedGenre: "",
  //   };
  // },
  props: {
    cditem: Array,
  },
  // computed: {
  //   dataOk() {
  //     return this.filteredGenres.length === 10 ? true : false;
  //   },
  // },
};
</script>

<style scoped lang="scss">
@import "@/styles/main";
</style>
