<template>
  <img
    :src="imagen"
    alt="No se puede ver"
  />

  <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
  <p>Recuerda que cuando finalices tu preguntas dar un ?</p>

  <h1>{{pregunta}}</h1>
  <h2>{{respuesta}}</h2>
</template>

<script>
export default {
  data() {
    return {
        pregunta:'',
        respuesta:null,
        imagen:'https://yesno.wtf/assets/yes/14-b57c6dc03aa15a4b18f53eb50d6197ee.gif'
    };
  },
  watch:{
    pregunta(value,oldValue){
        console.log(value);
        console.log(oldValue);
        if(value.includes('?')){
            //programar la llamada al API para obtener 
            //el SI o el NO, y la imagen
            console.log('AQUI LLAMO AL API');
            this.llamarAPI();
        }
    },
    async fachada(){
        await this.llamarAPI();
    }
  },
  methods:{
    async llamarAPI(){
        const data=await fetch('https://yesno.wtf/api').then((resp)=>resp.json());
        this.respuesta=data.answer;
        this.imagen= data.image;
        console.log(data);
    }
  }
};
</script>

<style>
</style>