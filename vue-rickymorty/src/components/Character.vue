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
  display: flex;
  margin: 0.2rem;
  padding: 1.5rem 1rem;
}

.imagen {
  border-radius: 50%;
  margin-right: 0.3rem;
}
h3 {
  font-size: 2em;
  margin-top: 6rem;
  margin-left: 2rem;
}
</style>
