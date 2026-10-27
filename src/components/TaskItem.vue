<script setup>
const tasques = defineProps({
  name: {
    type: String,
  },
  completed: {
    type: Boolean,
  },
  selected: {
    type: Boolean,
  }
});

const emit = defineEmits(['click', 'delete']);
</script>

<template>
  <div
    class="task-item"
    :class="{ completed: tasques.completed, selected: tasques.selected }"
    @click="emit('click')"
  >
  <p>Fer-ho amb la llista d'iteració</p>
    <span>{{ tasques.name }}</span>
    <button type="button" class="delete-btn" @click.stop="emit('delete')">
      Eliminar
    </button>
  </div>
</template>