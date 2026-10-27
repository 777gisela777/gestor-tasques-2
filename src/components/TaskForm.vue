<script setup>
import { ref } from 'vue';

const nom = ref('');
const emit = defineEmits(['enviarNom']);

const enviarNom = () => {
    emit('enviarNom', nom.value);
}
</script>

<template>
    <div class="form">
        <input v-model="nom" placeholder="Introdueix el nom de la tasca" />
        <button @click="enviarNom">Enviar</button>
    </div>
</template>