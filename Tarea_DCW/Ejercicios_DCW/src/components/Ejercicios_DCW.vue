<script setup>
// Ejercicio 1
import { ref, computed } from 'vue'

const precio = ref(0)
const descuento = ref(0)

const precioFinal = computed(() => {
  return precio.value - (precio.value * (descuento.value / 100))
})

// Ejercicio 2
const tareas = ref([
  { texto: 'Jugar Video Juegos', completada: true },
  { texto: 'Ver Series', completada: true },
  { texto: 'Leer un libro', completada: true },
  { texto: 'Dormir', completada: false }
])

const tareasCompletadas = computed(() => {
  return tareas.value.filter(t => t.completada)
})
</script>

<template>
  <div class="container">
    <h1 class="titulo">Ejercicios-DCW</h1>
    <!-- Ejercicio 1 -->
    <div class="card">
      <h2>Calculadora de Descuento</h2>
      <label>Precio original:</label>
      <input type="number" v-model="precio" />

      <label>Descuento (%):</label>
      <input type="number" v-model="descuento" />

      <p>Precio final: {{ precioFinal.toFixed(2) }}</p>
    </div>

    <!-- Ejercicio 2 -->
    <div class="card">
      <h2>Lista de Tareas</h2>
      <ul>
        <li v-for="(tarea, index) in tareasCompletadas" :key="index">
          {{ tarea.texto }}
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 1000px;
  margin: 0 auto;
  font-family: 'Segoe UI', sans-serif;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  color: #f1f1f1;
  align-items: center;
  position: relative;
  right: -150%;
}

.titulo {
  text-align: center;
  font-size: 2rem;
  color: #f1f1f1;
  margin-bottom: 1rem;
}

.card {
  background-color: #1e1e1e;
  border-radius: 12px;
  padding: 2.9rem;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
  width: 100%;
}

.card h2 {
  margin-bottom: 1rem;
  font-size: 1.5rem;
  color: #ffffff;
}

label {
  font-weight: bold;
  display: block;
  margin-top: 1rem;
  color: #ddd;
}

input {
  display: block;
  margin-top: 0.5rem;
  padding: 0.5rem;
  width: 100%;
  max-width: 300px;
  border: 1px solid #444;
  border-radius: 6px;
  font-size: 1rem;
  background-color: #2c2c2c;
  color: #f9f9f9;
}

input:focus {
  outline: none;
  border-color: #007bff;
}

p {
  margin-top: 1rem;
  font-size: 1.1rem;
  color: #00bfff;
}

ul {
  padding-left: 0;
  list-style-type: none;
}

li {
  margin: 0.5rem 0;
  padding: 0.5rem;
  background-color: #2a2a2a;
  color: #e4e4e4;
  border-radius: 6px;
}
</style>
