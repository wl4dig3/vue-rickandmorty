<template>
  <div class="contenedor">
    <img class="imagen" :src="src" alt />
    <h3 @click="avisaleApapa">{{name}} {{indice}}</h3>
  </div>
</template>

<script>
export default {
  name: "Character",
  props: {
    src: String,
    name: String,
    indice: String,
  },
  methods: {
    avisaleApapa() {
      this.$emit("toctoc", this.indice);
    },
  },
};
</script>

<style lang="scss" scoped>
.contenedor {
  // background-color: brown;
  display: flex;
  margin: .2rem;
  padding: 1.5rem 1rem;
}
  .imagen {
    border-radius: 50%;
    margin-right: .3rem;
  }
  h3 {
    font-size: 2em;
    margin-top: 6rem;
    margin-left: 2rem;
  }
</style>
