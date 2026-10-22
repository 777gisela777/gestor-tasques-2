<script setup>
import { ref } from 'vue'

const tasks = ref([
  { id: 1, nom: 'Menjar', completed: false },
  { id: 2, nom: 'Dormir', completed: true },
  { id: 3, nom: 'Fer esport', completed: false }
]);
</script>
