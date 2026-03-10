<template>
  <form>
    <div class="p-3 border rounded mb-4">
      <div class="form-group mb-2">
        <label>Título</label>
        <input v-model="newTitle" type="text" class="form-control" placeholder="Título">
      </div>
      <div class="form-group mb-2">
        <label>Contenido</label>
        <input v-model="newContent" type="text" class="form-control" placeholder="Contenido">
      </div>

      <button type="button" @click="addCard" class="btn btn-primary">Submit</button>
    </div>
  </form>


  <div class="mb-3" v-for="(card, index) in cards">
    <Card :id="card.id" :title="card.title" :content="card.content" />
    <button v-on:click="eliminar(card.id)" class="btn btn-secondary">Eliminar</button>

  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Card from './components/Card.vue';

const newTitle = ref('');
const newContent = ref('');


const cards = ref([
  {
    "id": 1,
    "title": "Exploración Espacial",
    "content": "Descubre los últimos avances en la misión a Marte y la tecnología de cohetes reutilizables.",
    //"image": "https://picsum.photos"
  },
  {
    "id": 2,
    "title": "Arquitectura Moderna",
    "content": "Un recorrido visual por los edificios más innovadores que están cambiando el skyline de las ciudades.",
    //"image": "https://picsum.photos"
  },
  {
    "id": 3,
    "title": "Gastronomía Local",
    "content": "Conoce los ingredientes secretos de la cocina tradicional y cómo se fusionan con técnicas modernas.",
    //"image": "https://picsum.photos"
  },
  {
    "id": 4,
    "title": "Inteligencia Artificial",
    "content": "Análisis sobre el impacto de los nuevos modelos de lenguaje en el trabajo creativo cotidiano.",
    //"image": "https://picsum.photos"
  }
]);

const addCard = () =>{

  if(!newTitle.value && !newContent.value) return alert('CAMPOS VACIOS');
  
  const newCard = {
    id: Date.now(),
    title: newTitle.value,
    content: newContent.value,
  };
  cards.value.push(newCard);

  newTitle.value = "";
  newContent.value = "";

}



const eliminar = (id: number) => {
  cards.value = cards.value.filter(xd => xd.id != id);
}


</script>

<style scoped></style>