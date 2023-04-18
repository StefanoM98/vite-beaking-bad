<script>
import { store } from "../store";
import YugiCard from "./YugiCard.vue";
import AppLoading from "./AppLoading.vue";
import axios from "axios";
export default {
  name: "AppMain",
  components: {
    YugiCard,
    AppLoading,
  },
  data() {
    return {
      store,
      selectedOptions: ["Alien", "Ally, of Justice", "Ancient Gear"],
      cardsFounded: 0,
      selectedArchetype: "",
    };
  },
  mounted() {
    this.getCard();
  },
  methods: {
    getArchetype() {
      store.loading = true;
      if (this.selectedArchetype) {
        axios
          .get(store.apiURL, {
            params: {
              archetype: this.selectedArchetype,
            },
          })
          .then((resp) => {
            this.store.cards = resp.data.data;
            this.cardsFounded = resp.data.meta.current_rows;
            store.loading = false;
          });
      } else {
        this.getCard();
      }
    },
    getCard() {
      axios.get(store.apiURL).then((resp) => {
        this.store.cards = resp.data.data;
        this.cardsFounded = resp.data.meta.current_rows;
      });
    },
  },
};
</script>

<template>
  <main>
    <div class="container p-4">
      <div class="container-fluid p-5">
        <select
          class="form-select"
          name="option"
          id="option"
          v-model="selectedArchetype"
          @change="getArchetype"
        >
          <option value="">All</option>
          <option v-for="option in selectedOptions" :value="option">
            {{ option }}
          </option>
        </select>
        <h3 class="found p-2">
          Founded <span>{{ cardsFounded }}</span> cards
        </h3>
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
