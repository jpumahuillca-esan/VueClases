<template>
  <h1 :class="detectarCambio" >Ahorros: {{ ahorros }} </h1>
  <button @click="aumentar(500)" class="btn btn-success">Aumentar</button>
  <button @click="disminuir(500)" class="btn btn-danger">Disminuir</button>

    

</template>

<script setup lang="ts">
import { ref,computed } from 'vue';
const ahorros = ref(100);

const aumentar = (cantidad: number) => {
  ahorros.value += cantidad;
}

const disminuir = (cantidad: number) => {
  ahorros.value -= cantidad;
}

const detectarCambio = computed (() =>{
  if(ahorros.value >=3500){
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