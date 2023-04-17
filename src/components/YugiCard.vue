<script>
export default {
  name: "YugiCard",
  props: {
    card: Object,
  },
};
</script>

<template>
  <div class="text-center card">
    <img :src="card.card_images[0].image_url_small" alt="" />
    <h4>{{ card.name }}</h4>
    <p>{{ card.archetype }}</p>
  </div>
</template>

<style scoped lang="scss">
.card {
  background-color: #d48f38;
  height: 100%;
  h4 {
    color: white;
    padding: 1rem;
    text-transform: uppercase;
    font-size: 0.9rem;
  }
}
</style>
