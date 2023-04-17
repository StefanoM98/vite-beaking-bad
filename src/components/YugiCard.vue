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
    <img :src="card.card_images.image_url_cropped" alt="" />
    <h4>{{ card.name }}</h4>
    <p>{{ card.archetype }}</p>
  </div>
</template>

<style scoped>
.card {
  background-color: #d48f38;
}
</style>
