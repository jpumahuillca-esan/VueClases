# Masterclass: Arquitectura Frontend Profesional con Vue 3

Esta guía detalla la implementación técnica de componentes reactivos utilizando Composition API y TypeScript.

## 1. El Template: Declaratividad y Estructura

El '< template >' es la capa de presentación. En nuestra arquitectura, lo separamos de la lógica para mantener el DOM limpio.

### v-model: Sincronización Bidireccional
Utilizamos v-model para vincular los inputs de formulario con nuestras variables reactivas. Esto elimina la necesidad de listeners manuales.

``` html
<input v-model="newTitle" type="text" class="form-control" placeholder="Título">
```

### Manejo de Eventos: @click
Los eventos se disparan mediante directivas. En nuestro caso, la función addCard es un manejador que procesa el estado actual del formulario.

``` html
<button type="button" @click="addCard" class="btn btn-primary">Submit</button>
```

## 2. Renderizado de Listas: v-for

El v-for permite generar elementos del DOM dinámicamente desde un array.

### Regla de Oro: La importancia de :key
Cada iteración debe tener un :key único. Esto permite a Vue identificar qué nodos del DOM pertenecen a qué objeto del array, optimizando la reconstrucción cuando eliminamos elementos.

``` html

<div class="mb-3" v-for="(card, index) in cards" :key="card.id">
<Card :id="card.id" :title="card.title" :content="card.content" />
<button @click="eliminar(card.id)" class="btn btn-secondary">Eliminar</button>
</div>
```

## 3. Lógica Condicional: v-if

Para mejorar la experiencia de usuario (UX), usamos v-if para ocultar elementos que no tienen datos o estados vacíos.

### Ejemplo de uso profesional:
``` html

<div v-if="cards.length > 0">
</div>
<div v-else>
<p>No tienes tarjetas creadas. ¡Empieza a escribir!</p>
</div>
```

## 4. Reactividad Avanzada: computed()

Las propiedades computadas son funciones que devuelven un valor basado en otras variables reactivas. Su ventaja sobre las funciones normales es que son reactivas y con caché. Si los datos (cards) no cambian, Vue devuelve el valor almacenado en lugar de ejecutar la función de nuevo.

``` typescript
import { computed } from 'vue';

// Ejemplo: Contador de tarjetas automático
const totalCards = computed(() => cards.value.length);
```

## 5. Lógica de Negocio y Estado (TypeScript)

En el ''<script setup lang="ts"></script>', gestionamos el ciclo de vida de los datos.

### addCard: Gestión de estados
Validamos antes de mutar. Usamos Date.now() para IDs únicos, lo cual es una técnica estándar en prototipado rápido.

``` typescript
const addCard = () => {
if(!newTitle.value && !newContent.value) return alert('CAMPOS VACIOS');

cards.value.push({
id: Date.now(),
title: newTitle.value,
content: newContent.value,
});

newTitle.value = "";
newContent.value = "";
}
```

### eliminar: Inmutabilidad
Al usar .filter(), generamos un nuevo array. Esto es mejor para la arquitectura de Vue, ya que facilita que el sistema de reactividad detecte que el array ha cambiado por completo.

``` typescript
const eliminar = (id: number) => {
cards.value = cards.value.filter(c => c.id != id);
}
```