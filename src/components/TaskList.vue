<script setup>
import { ref } from 'vue';
const tasks = defineProps({
  tasques: Array
})
</script>

<template>
  <ul>
    <li v-for="task in tasques" :key="task.id">
      <p v-if="task.completed">{{ task.nom }} - Completada</p>
      <p v-else="!task.completed">{{ task.nom }} - Pendent</p>
      <p>Pendent modificar botons eliminar/canviar estat (passar-los amb props de pare a fill)</p>
      <button v-on:click="canviarEstatTasca(task)">
        {{ task.completed ? 'Marcar com a pendent' : 'Marcar com a completada' }}
      </button>
      <button v-on:click="eliminarTasca(task)">Eliminar</button>
    </li>
  </ul>

</template>