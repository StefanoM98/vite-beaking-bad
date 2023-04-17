<script>
import YugiCard from "./YugiCard.vue";
import { store } from "../store";
import AppLoading from "./AppLoading.vue";
export default {
  name: "AppMain",
  components: {
    YugiCard,
    AppLoading,
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
        <h3 class="found p-2">Found 20 cards</h3>
        <AppLoading v-if="store.loading" />
        <div class="row row-cols-5" v-else>
          <div class="col mb-3" v-for="card in store.cards">
            <YugiCard :card="card" />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
.container {
  width: 100%;
  height: 100%;
  background-color: #d48f38;
  .container-fluid {
    background-color: white;
    .found {
      background-color: #212529;
      color: white;
    }
  }
}
</style>
