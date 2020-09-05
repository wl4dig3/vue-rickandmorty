<template>
  <div class="body">
    <h1>Welcome to the Rick and Morty's world</h1>
    <input v-model="indice" type="text" />

    <div v-for="(p, i) in personajes" :key="i">
      <Character class="jaja" @toctoc="saludar" :src="p.picture" :name="p.nombre" :indice="indice" />
    </div>
  </div>
</template>

<script>
import Character from "./components/Character";
export default {
  components: {
    Character,
  },
  data() {
    return {
      personajes: [],
      indice: "",
    };
  },
  methods: {
    saludar(indice) {
      this.personajes.splice(indice, 1);
    },
  },
  mounted() {
    fetch("https://rickandmortyapi.com/api/character")
      .then((response) => response.json())
      .then((json) => {
        let data = json.results;

        data.slice(0, 10).forEach((el) => {
          let nombre = el.name;
          let picture = el.image;

          this.personajes.push({
            nombre,
            picture,
          });
        });
      })
      .catch((err) => {
        console.log(`todo esta perdido rick ${err}`);
      });
  },
};
</script>

<style lang="scss" scoped>
.body {
  background-image: url("../src/assets/bg-ricky.jpg");
  background-size: contain;
  display: flex;
  flex-direction: column;
  color: white;

  h1 {
    text-align: center;
    color: white;
    padding: 1rem;
  }
}
</style>