<script setup>
import { ref } from "vue";

const nuevaTarea = ref("");
const tareas = ref([]);
let siguienteId = 1;

function agregarTarea() {
  const texto = nuevaTarea.value.trim();
  if (texto === "") return;
  tareas.value.push({ id: siguienteId++, texto, completa: false });
  nuevaTarea.value = "";
}
</script>

<template>
  <h1>Mis Tareas</h1>
  <form @submit.prevent="agregarTarea">
    <input v-model="nuevaTarea" placeholder="Escribe una tarea" />
    <button>Agregar</button>
  </form>

  <p v-if="tareas.length === 0">No hay tareas todavía</p>
  <ul>
    <li v-for="tarea in tareas" :key="tarea.id"> {{ tarea.texto }}</li>
  </ul>
</template>
