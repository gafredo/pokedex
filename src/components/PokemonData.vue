<template>
  <h1 class="pokemon__data">
    <span class="pokemon__number">{{ number }}</span> -
    <span class="pokemon__name">{{ name }}</span>
  </h1>
</template>

<script>
export default {
  name: 'PokemonData',
  props: ['number', 'name'],
};
</script>

<style scoped>
.pokemon__data {
  position: absolute;
  font-weight: 600;
  color: #aaa;
  top: 54.5%;
  right: 27%;
  font-size: clamp(8px, 5vw, 25px);
}

.pokemon__name {
  color: #3a444d;
  text-transform: capitalize;
}
</style>
