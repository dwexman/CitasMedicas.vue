<template>
  <div class="cita-card" :style="{ backgroundColor: obtenerColor(cita.gravedad) }">
    <p><strong>Paciente:</strong> {{ cita.paciente }}</p>
    <p><strong>Fecha:</strong> {{ cita.fecha }}</p>
    <p><strong>Hora:</strong> {{ cita.hora }}</p>
    <p><strong>Gravedad:</strong> {{ cita.gravedad }}</p>
    <p><strong>Motivo:</strong> {{ cita.motivo }}</p>
    <button @click="$emit('eliminar-cita')" class="eliminar-btn">Eliminar</button>
  </div>
</template>

<script>
export default {
  props: {
    cita: Object
  },
  methods: {
    obtenerColor(gravedad) {
      if (gravedad === 'Baja') return 'green';
      if (gravedad === 'Media') return 'yellow';
      if (gravedad === 'Alta') return 'red';
      return 'white';
    }
  }
};
</script>

<style scoped>
.cita-card {
  padding: 15px;
  margin-bottom: 15px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  color: #333;
}
.eliminar-btn {
  background-color: #ff6b55;
  color: white;
  border: none;
  padding: 8px 15px;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}
</style>
