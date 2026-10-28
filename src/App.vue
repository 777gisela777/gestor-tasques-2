<script setup>
import TaskList from './components/TaskList.vue'
import Formulari from './components/TaskForm.vue'
import { ref, computed } from 'vue';

const tasks = ref([
  { id: 1, nom: 'Menjar', completed: false },
  { id: 2, nom: 'Dormir', completed: true },
  { id: 3, nom: 'Fer esport', completed: false }
]);

const mostrarPendents = ref(false);

const tasquesCompletades = computed(() => tasks.value.filter(task => task.completed).length);
const tasquesPendents = computed(() => tasks.value.filter(task => !task.completed).length);
const tasquesVisibles = computed(() =>
  mostrarPendents.value ? tasks.value.filter(task => !task.completed) : tasks.value
);

const afegirTasca = (nom) => {
 if (!nom || !nom.trim()) return;
 tasks.value.push({
  id: tasks.value.length + 1,
  nom: nom.trim(),
  completed: false
 });
}

const canviarEstatTasca = (id) => {
  const task = tasks.value.find((task) => task.id === id)
  if (task) task.completed = !task.completed

}

const eliminarTasca = (id) => {
  tasks.value = tasks.value.filter(task => task.id !== id);
}
</script>

<template>
  <h1>Tasques</h1>
  <Formulari @addTask="afegirTasca" />
  <div class="tasks-list">
    <label>
      <input v-model="mostrarPendents" type="checkbox">
      Mostrar només pendents
    </label>
    <TaskList 
    :tasks="tasquesVisibles"
    @modifyTaskStatus="canviarEstatTasca"
    @deleteTask="eliminarTasca"
    />
  </div>
    <p>Total: {{ tasks.length }} | Tasques completades: {{ tasquesCompletades }}| Tasques pendents: {{ tasquesPendents }}</p>
</template>

<style scoped>
:global(body) {
  background: #BFBFBF;
  color: #24312b;
  font-family: system-ui, sans-serif;
  line-height: 1.5;
  justify-content: center;
  align-items: center;
  display: flex;
}

label {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 16px 0;
}

input[type='checkbox'] {
  accent-color: #564256;
}

p {
    color: black;
}
</style>
