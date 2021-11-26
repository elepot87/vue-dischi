<template>
  <div class="header p-2">
    <img src="../assets/logo.png" alt="logo" class="logo" />
    <div class="container-select">
      <select name="selection" id="select-genre">
        <option value="">All genres</option>
        <option value="rock">Rock</option>
        <option value="pop">Pop</option>
        <option value="metal">Metal</option>
        <option value="jazz">Jazz</option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped lang="scss">
@import "@/styles/header";
</style>
