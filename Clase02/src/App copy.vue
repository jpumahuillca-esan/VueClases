<template>
  <h1 :class="asignarColor">Ahorros: {{ ahorros }}</h1>
  <button @click="depositar">depositar</button>
  <button @click="disminuir">disminuir</button>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue';

const ahorros = ref(1000);

const depositar = () => {
  ahorros.value += 500;
}
const disminuir = () => {
  ahorros.value -= 500;
}


const asignarColor = computed (() =>{
  if(ahorros.value > 1500){
    return 'verde'
  }
  return 'rojo'
})

</script>

<style scoped>
.verde{
  color: green;
}
.rojo{
  color: red;
}
</style>