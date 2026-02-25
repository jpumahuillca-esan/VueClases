<<<<
# Masterclass: Desarrollo Web con Vue 3 🚀

Guía completa para dominar los fundamentos de Vue.js, Composition API y TypeScript.

## 🛠️ 1. Instalación y Configuración
El comando principal para iniciar proyectos modernos es:

``` bash
npm create vue@latest
```

### Pasos obligatorios:
``` bash
cd nombre-del-proyecto
```
``` bash
npm install
``` 
``` bash
npm run dev
``` 
## 🧊 2. El núcleo: Reactividad con ref()
En Vue 3, una variable común no actualiza el DOM. Usamos ref para crear una referencia reactiva.

``` typescript
import { ref } from 'vue';
// Definición: ref(valor_inicial)
const contador = ref<number>(0);
// IMPORTANTE: En el script SIEMPRE usamos .value
const sumar = () => {
contador.value++;
}



```

## 🚦 3. Directivas de Control

### v-if, v-else-if, v-else
Para lógica condicional directamente en el HTML:
``` html
<p v-if="contador === 0">No hay clics aún</p>
<p v-else-if="contador < 10">¡Sigue presionando!</p>
<p v-else>¡Nivel experto alcanzado!</p>
```

### v-for (Renderizado de listas)
Itera sobre arreglos o rangos. Regla de oro: Siempre usa :key.
``` html

<div v-for="n in contador" :key="n">
Iteración número {{ n }}
</div>
```

## 🎨 4. Clases Dinámicas y Estilos
Para sombrear o resaltar elementos según el estado, usamos :class.

``` html
<button
class="btn"
:class="contador >= 10 ? 'btn-success' : 'btn-danger'"

{{ contador >= 10 ? 'META ALCANZADA' : 'PENDIENTE' }}
</button>
```

## 🧩 5. Comunicación: Props y v-model

### Props (Padre a Hijo)
Permiten pasar datos a componentes reutilizables.
``` typescript
// En el componente Hijo
defineProps<{ titulo: string }>();
```

### v-model (Inputs)
Crea una conexión de doble vía entre el input y la variable.

``` html
<input type="number" v-model.number="contador">
```

## ⚡ 6. Eventos Comunes

@click: Al hacer clic.

@submit.prevent: Para formularios sin recargar página.

``` typescript
import { ref } from 'vue'; 
const valor = ref(0);  
const sumar = () => {
  valor.value++; 
};
```

``` html
<button @click="sumar">Ejecutar Función</button>
<h1>{{ valor}}</h1>
```

<<<<