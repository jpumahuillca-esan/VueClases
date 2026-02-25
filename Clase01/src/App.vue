<template>
  <div>
    <h1>{{ num }}</h1>
    <button @click="incrementar" class="btn btn-success">INCREMENTAR</button>
    <button @click="disminuir" class="btn btn-danger">DISMINUIR</button>
    <Card :link="'https://www.vuemastery.com/pricing/?coupon=40off_2025'" :title="'TITULO1'" :content="'Contenido 123'" :name-buton="'CESAR '"/>
    <Card :link="'https://www.vuemastery.com/pricing/?coupon=40off_2025'" :title="'4123123'" :content="'Contenido 12413123'"/>
    <Card :link="'https://www.vuemastery.com/pricing/?coupon=40off_2025'" :title="'Titulo3'" :content="'Contenido 4'"/>
  </div>
</template>

<script setup lang="ts">
  import Card from './components/Card.vue';

  import { ref } from 'vue';

  const num = ref(0);

  const incrementar = () =>{
    num.value++;
  }
    const disminuir = () =>{
    num.value <= 0 ? alert ("Ya no puedes bajar mas") : num.value--;
  }


</script>

<style scoped>

</style>