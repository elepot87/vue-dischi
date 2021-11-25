<template>
  <div>
    <div class="card-cd">
      <div class="cover-cd">
        <img :src="image" :alt="title" />
      </div>
      <div class="info-cd text-center mt-3">
        <div class="title-cd mb-2 text-uppercase">
          {{ title }}
        </div>
        <div class="author mb-1">{{ subtitle }}</div>
        <div class="year mb-1">{{ info1 }}</div>
        <div class="genre mb-1">{{ info2 }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    image: String,
    title: String,
    subtitle: String,
    info1: String,
    info2: String,
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/card";
</style>
