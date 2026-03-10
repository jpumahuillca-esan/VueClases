<template>
  <!--
  <h1 :class="detectarCambio" >Ahorros: {{ ahorros }} </h1>
  <button @click="aumentar(500)" class="btn btn-success">Aumentar</button>
  <button @click="disminuir(500)" class="btn btn-danger">Disminuir</button>
  -->
  <div>
    <h2>NUMERO DEL 1 AL 100</h2>
    <span v-for="value in 100">
      {{ value }} - 
    </span>

    <div v-for="(card,index) in cards">
      <Card :title="card.title" :content="card.content" />
    </div>
  </div>


</template>

<script setup lang="ts">

const name = "Jhardel";

const array = ['Juan',14,true];

const cards = ref([
  {
    "id": 1,
    "title": "Exploración Espacial",
    "content": "Descubre los últimos avances en la misión a Marte y la tecnología de cohetes reutilizables.",
    //"image": "https://picsum.photos"
  },
  {
    "id": 2,
    "title": "Titulo2",
    "content": "Descubre los últimos avances en la misión a Marte y la tecnología de cohetes reutilizables.",
    //"image": "https://picsum.photos"
  },
    {
    "id": 3,
    "title": "Titulo3",
    "content": "Descubre los últimos avances en la misión a Marte y la tecnología de cohetes reutilizables.",
    //"image": "https://picsum.photos"
  }
]);



import Card from './components/Card.vue';


import { ref,computed } from 'vue';

const ahorros = ref(100);

const aumentar = (cantidad: number) => {
  ahorros.value += cantidad;
}

const disminuir = (cantidad: number) => {
  ahorros.value -= cantidad;
}

const detectarCambio = computed (() =>{
  if(ahorros.value >=1500){
    return 'verde';
    
  }
  return 'red';
})







</script>

<style scoped>
.verde{
  color:green;
}
.red{
  color:red;
}


</style>