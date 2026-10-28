<script setup>
import { ref } from 'vue';

const tascaNova = ref('');
const emit = defineEmits(['addTask']);

const enviarTasca = () => {
    const nom = tascaNova.value.trim()
    if (!nom) return
    emit('addTask', nom);
    tascaNova.value = ''
}
</script>

<template>
    <div class="form">
        <label for="tascaNova">Afegir una nova tasca</label>
        <input id="tascaNova" v-model="tascaNova" placeholder="Introdueix el nom de la tasca" />
        <button type="button" @click="enviarTasca">Afegir</button>
    </div>
</template>
<style scoped>
input:not([type='checkbox']) {
  display: flex;
  align-items: center;
  gap: 8px;
  width: min(100%, 26rem);
  padding: 9px 11px;
  border: 1px solid #cbd5ce;
  border-radius: 5px;
  font: inherit;
}

label {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 0px 0px 16px 0px;
}

button {
  margin: 6px 6px 6px 0;
  padding: 8px 12px;
  border: 0;
  border-radius: 5px;
  background: #564256;
  color: #fff;
  font: inherit;
  cursor: pointer;
}

button:hover {
  background: #3d2f3d;
}

p {
    color: black;
}
</style>