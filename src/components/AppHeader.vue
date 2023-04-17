<script>
export default {
  name: "AppHeader",
};
</script>

<template>
  <div class="container d-flex align-items-center">
    <img src="../assets/img/yugi.jpeg" alt="" />
    <h1>Yu-Gi-Oh API</h1>
  </div>
</template>

<style scoped lang="scss">
.container {
  height: 70px;
  background-color: lightblue;
  h1 {
    font-weight: 700;
  }
  img {
    width: 100px;
  }
}
</style>
