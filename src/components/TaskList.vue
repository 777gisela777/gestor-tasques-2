<script setup>
import { ref } from 'vue';
import TaskItem from './TaskItem.vue';

const tasques = defineProps({
  tasks: {
    type: Array,
    default: () => []
  }
});

const selectedTask = ref();
const emit = defineEmits(['eliminarTasca']);

const selectTask = (task) => {
  selectedTask.value = task;
};

const deleteTask = (id) => {
  emit('eliminarTasca', id);
};
</script>

<template>
  <div class="tasks">
    <TaskItem
      v-for="task in tasques.tasks"
      :key="task.id"
      :name="task.nom"
      :completed="task.completed"
      :selected="task.id === selectedTask?.id"
      @click="selectTask(task)"
      @delete="deleteTask(task.id)"
    />
  </div>
</template>


