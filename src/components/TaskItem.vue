<script setup>
defineProps({
  task: {
    type: Object,
    required: true,
  }
});

const emit = defineEmits(['modifyTaskStatus', 'deleteTask']);
</script>

<template>
  <div
    class="taskItem"
    :class="{ completed: task.completed }"
  >
      <p v-if="task.completed">{{ task.nom }} - Completada</p>
      <p v-else="!task.completed">{{ task.nom }} - Pendent</p>
      <button type="button" @click="emit('modifyTaskStatus', task.id)">
        {{ task.completed ? 'Marcar com a pendent' : 'Marcar com a completada' }}
      </button>
    <button type="button" class="deleteButton" @click="emit('deleteTask', task.id)">
      Eliminar
    </button>
  </div>
</template>
<style scoped>
button {
  margin: 0 6px 6px 0;
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