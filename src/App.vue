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
 if (!nom || !nom.trim()) return;
 tasks.value.push({
  id: Date.now(),
  nom: nom.trim(),
  completed: false
 });
}

provide('nom', nomTasca);

const eliminarTasca = (id) => {
  tasks.value = tasks.value.filter(task => task.id !== id);
}
</script>

<template>
  <h1>Tasques</h1>
  <p>Afegir una nova tasca</p>
  <Formulari @enviarNom="gestionarNom" />
  <div class="tasks-list">
    <TaskList 
    :tasks="tasks"
    @eliminarTasca="eliminarTasca"
    />
  </div>
</template>
<style scoped></style>
