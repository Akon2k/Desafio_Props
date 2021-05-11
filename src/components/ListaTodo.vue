<template>
  <div class="hello">
    <h1>{{ mensaje }}</h1>
    <label>Tarea:</label>
    <input
      type="text"
      v-model="inputMensaje"
      placeholder="Agregar nueva tarea"
    />
    <button @click="agregar">Agregar</button>
    <br />
    <hr />
    <h1>Lista</h1>
    <div>
      <ul>
        <ListaItem
          v-for="(nombre, i) in lista"
          :key="i"
          :nombre="nombre"
          :indice="i"
          v-on:borrar="borrar"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import ListaItem from "./ListaItem.vue";

export default {
  name: "ListaTodo",
  data() {
    return {
      lista: [],
      inputMensaje: "",
    };
  },
  components: {
    ListaItem,
  },
  methods: {
    agregar() {
      if (this.inputMensaje) {
        this.lista.push(this.inputMensaje);
        this.inputMensaje = "";
      }
    },
    borrar(i) {
      this.lista = this.lista.filter((item, index) => i !== index);
    },
  },
  props: {
    mensaje: String,
  },
};
</script>

<style scoped>
h3 {
  margin: 20px;
}
ul {
  padding: 0;
  list-style-type: none;
}
li {
  margin: 10px 10px;
}

input {
  margin: 0 10px;
}
</style>
