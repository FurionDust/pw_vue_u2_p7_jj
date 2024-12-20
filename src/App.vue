<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <Contador
    encabezado="Contador Primero"
    :valor="calcular(1, 2)"
    :esVerdad="muestraPrimero"
    :valor2="78"
  />
  <Contador
    encabezado="Contador Segundo"
    :valor="calcular(3, 2)"
    :esVerdad="muestraSegundo"
  />
  <button @:click="cambiar(1)">Cambiar Primero</button>
  <button @:click="cambiar(2)">Cambiar Segundo</button>
</template>

<script>
import Contador from "./components/Contador.vue";

export default {
  name: "App",
  components: {
    Contador,
  },
  methods: {
    calcular(a, b) {
      return a + b;
    },
    cambiar(valor) {
      if (valor === 1) {
        this.muestraPrimero = !this.muestraPrimero;
      } else {
        this.muestraSegundo = !this.muestraSegundo;
      }
    },
  },
  data() {
    return {
      muestraPrimero: true,
      muestraSegundo: true,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>