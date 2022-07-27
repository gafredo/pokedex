<template>
  <img :src="img_url" alt="pokemon" class="pokemon__image" />
</template>

<script>
export default {
  name: 'PokemonImg',
  props: ['img_url'],
};
</script>

<style scoped>
.pokemon__image {
  position: absolute;
  bottom: 55%;
  left: 50%;
  transform: translate(-63%, 20%);
  height: 18%;
}
</style>
