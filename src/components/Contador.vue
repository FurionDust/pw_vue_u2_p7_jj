<template>
  <h2>{{ encabezado }} : {{ valor2 }}</h2>
  <p>{{ numero }} <sup>2</sup>={{ calcularCuadradoComputado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ calcularCuadradoComputado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ calcularCuadradoComputado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ calcularCuadradoComputado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ calcularCuadradoComputado }}</p>
  <div>
    <button v-on:click="incrementar()">+1</button>
    <button v-on:click="decrementar()">-1</button>
  </div>
  <div v-if="esVerdad">
    <h1>FELIZ NAVIDAD PARA TODOS USTEDES</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero: this.valor,
      titulo: "Contador",
    };
  },
  methods: {
    calcularCuadrado() {
      console.log("Entro a calcular");
      return this.numero * this.numero;
    },
    incrementar() {
      this.numero++;
    },
    decrementar() {
      this.numero--;
    },
  },
  computed: {
    calcularCuadradoComputado() {
      console.log("Entro a calcular computado");
      return this.numero * this.numero;
    },
  },
  //props:['encabezado','valor' ]
  props: {
    encabezado: {
      type: String,
      validator(value) {
        return value.includes("a");
      },
    },
    valor: Number,
    valor2: {
      type: Number,
      required: false,
      default: 77,
      validator(value) {
        //programo mi validacion bajo mi criterio y retorno true
        //cuando es valido para mi
        //retorno false cuando no se valido para mi
        return value <= 77;
      },
    },
    esVerdad: {
      type: Boolean,
      required: true,
    },
    arreglo: Array,
    fecha: Date,
    objetoPersona: Object,
  },
};
</script>

<style>
button {
  background: #64b687;
  border-radius: 5px;
  border: 1px solid #ffffff;
  cursor: pointer;
  margin: 0px 5px;
  padding: 5px 15px;
  box-shadow: 2px 2px #2c3e50;
}
button:hover {
  background: #5aa67b;
}
</style>