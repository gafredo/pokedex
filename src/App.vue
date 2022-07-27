<template>
  <main>
    <img
      src="https://i.gifer.com/WnES.gif"
      alt="pokemon"
      class="pokemon__image"
    />
    <h1 class="pokemon__data">
      <span class="pokemon__number">6</span> -
      <span class="pokemon__name">bulbasaur</span>
    </h1>

    <img src="./assets/pokedex.png" alt="pokedex" class="pokedex" />
  </main>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Oxanium:wght@300;400;500;600;700;800&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Oxanium', cursive;
}

body {
  text-align: center;
  background: linear-gradient(to bottom, rgb(0, 153, 255), #fff);
  min-height: 100vh;
}

main {
  display: inline-block;
  margin-top: 2%;
  padding: 15px;
  position: relative;
}
.pokedex {
  width: 100%;
  max-width: 425px;
}

.pokemon__image {
  position: absolute;
  bottom: 55%;
  left: 50%;
  transform: translate(-63%, 20%);
  height: 18%;
}

.pokemon__data {
  position: absolute;
  font-weight: 600;
  color: #aaa;
  top: 54.5%;
  right: 27%;
}

.pokemon__name {
  color: #3a444d;
  text-transform: capitalize;
}
</style>
