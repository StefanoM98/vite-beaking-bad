<script>
import YugiCard from "./YugiCard.vue";
import { store } from "../store";
export default {
  name: "AppMain",
  components: {
    YugiCard,
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <main>
    <div class="container p-4">
      <select class="form-select" aria-label="Default select example">
        <option selected>Scegli un archetipo</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
      </select>

      <div class="container-fluid p-5">
        <div class="row row-cols-5">
          <div class="col" v-for="card in store.cards">
            <YugiCard class="card" :card="card" />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
.container {
  width: 100%;
  height: calc(100vh - 70px);
  background-color: #d48f38;
  .container-fluid {
    height: 700px;
    background-color: white;
  }
}
</style>
