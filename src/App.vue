<template>
  <main>
    <a href="https://youtu.be/SjtdH3dWLa8?t=1463">Video</a>
    <!-- <img :src="img_url" alt="pokemon" class="pokemon__image" /> -->

    <PokemonImg :img_url="img_url" />;

    <PokemonData :number="number" :name="name" />

    <form class="form" @submit.prevent="">
      <PokemonInput @search="findPokemon" />
    </form>

    <div class="buttons">
      <PokemonBtn caption="&lt; Prev" inc="-1" @click="changePokemon" />
      <PokemonBtn caption="Next >" inc="1" @click="changePokemon" />
    </div>

    <img src="./assets/pokedex.png" alt="pokedex" class="pokedex" />
  </main>
</template>

<script>
import PokemonImg from './components/PokemonImg.vue';
import PokemonInput from './components/PokemonInput.vue';
import PokemonBtn from './components/PokemonBtn.vue';
import PokemonData from './components/PokemonData.vue';

export default {
  name: 'App',
  components: {
    PokemonImg,
    PokemonInput,
    PokemonBtn,
    PokemonData,
  },
  data() {
    return {
      number: 1,
      name: '',
      img_url: '',
    };
  },
  methods: {
    async getPokemon(pokemon) {
      pokemon = pokemon.toString();
      const resp = await fetch(
        `https://pokeapi.co/api/v2/pokemon/${pokemon.toLowerCase()}`
      );

      if (resp.status === 404) {
        this.name = 'NotFound :(';
        this.number = '';
        this.img_url = '';
        return;
      }
      const data = await resp.json();
      this.name = data.name;
      this.number = data.id;
      this.img_url =
        data['sprites']['versions']['generation-v']['black-white']['animated'][
          'front_default'
        ];
    },
    changePokemon(e) {
      const num = e.num * 1;
      this.number += num;
      if (this.number <= 0) this.number = 1;
      else this.getPokemon(this.number);
    },
    findPokemon(e) {
      this.getPokemon(e.text);
      this.search = '';
    },
  },
  created() {
    this.getPokemon(this.number);
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Oxanium:wght@300;400;500;600;700;800&display=swap');

a {
  position: absolute;
  bottom: 0;
  left: 41%;
}

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

.form {
  position: absolute;
  width: 65%;
  top: 65%;
  left: 13.5%;
}

.buttons {
  position: absolute;
  bottom: 10%;
  left: 50%;
  width: 65%;
  transform: translate(-57%, 0);
  display: flex;
  gap: 20px;
}
</style>
