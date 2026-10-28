<script setup>
import TaskItem from './TaskItem.vue';

const props = defineProps({
  tasks: {
    type: Array,
    default: () => []
  }
});

const emit = defineEmits(['modifyTaskStatus', 'deleteTask']);

function enviarCanviEstat(id) {
  emit('modifyTaskStatus', id)
}

function enviarEliminar(id) {
  emit('deleteTask', id)
}

</script>

<template>
  <div class="tasks">
    <TaskItem
      v-for="task in props.tasks"
      :key="task.id"
      :task="task"
      @modifyTaskStatus="enviarCanviEstat"
      @deleteTask="enviarEliminar"
    />
  </div>
</template>