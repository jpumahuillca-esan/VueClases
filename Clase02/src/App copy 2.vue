<template>
  <h1>Ahorros -> {{ ahorros }}</h1>
  <button @click="depositar(100)">Depositar +100</button>
  <button @click="retirar(100)" :disabled="disabledButton">Retirar -100</button>
  <div>
    <h4>Movimientos:</h4>
    <ul>
      <li v-for="(movimiento,index) in invertirArrary" :key="index">
        Monto {{}}{{ movimiento.monto }} -> {{ movimiento.saldoActual }} Saldo Actual
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

const ahorros = ref(0);
const movimientos = ref<IMovimiento[]>([]);

interface IMovimiento{
  monto: number;
  saldoActual:number;
};

const depositar = (cantidad: number) => {
  ahorros.value += cantidad;
  movimientos.value.push({
    monto: cantidad,
    saldoActual: ahorros.value
  })
};
const retirar = (cantidad: number) => {
  ahorros.value -= cantidad;
    movimientos.value.push({
    monto: -cantidad,
    saldoActual: ahorros.value
  })
};


const invertirArrary = computed(() =>{
  return movimientos.value.reverse();
})

const disabledButton = computed(() =>{
   return ahorros.value <= 0 ? true : false;
});



</script>

<style scoped></style>