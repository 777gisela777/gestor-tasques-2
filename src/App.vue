<script setup>
import TaskList from './components/TaskList.vue'
import Formulari from './components/TaskForm.vue'
import { ref, provide } from 'vue';

const tasks = ref([
  { id: 1, nom: 'Menjar', completed: false },
  { id: 2, nom: 'Dormir', completed: true },
  { id: 3, nom: 'Fer esport', completed: false }
]);

const nomTasca = ref('');

const gestionarNom = (nom) => {
  nomTasca.value = nom;
}

provide('nom', nomTasca);
</script>

<template>
  <h1>Tasques</h1>
  <p>Afegir una nova tasca</p>
  <Formulari @enviarNom="gestionarNom" />
  <div class="tasks-list">
    <TaskList :tasques="tasks"/>
  </div>
</template>
<style scoped></style>
