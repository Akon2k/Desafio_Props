<template>
  <li>{{ nombre }} <button @click="clickEBorrar(indice)">Borrar</button></li>
</template>

<script>
export default {
  name: "listaitem",
  props: {
    nombre: String,
    indice: Number,
  },
  methods: {
    clickEBorrar(indice) {
      this.$emit("borrar", indice);
    },
  },
};
</script>
