<template>
  <div class="container">
    <h1>Administrador de Citas Médicas</h1>

    <!-- Componente de formulario de pacientes -->
    <PatientForm @add-cita="agregarCita" />

    <!-- Mostrar mensaje si no hay citas -->
    <p v-if="citas.length === 0">Aún no hay consultas registradas</p>

    <!-- Mostrar las citas en formato de tarjeta -->
    <div class="citas-container">
      <CitaCard
        v-for="(cita, index) in citas"
        :key="index"
        :cita="cita"
        @eliminar-cita="eliminarCita(index)"
      />
    </div>
  </div>
</template>

<script>
import PatientForm from './components/PatientForm.vue';
import CitaCard from './components/CitaCard.vue';

export default {
  components: {
    PatientForm,
    CitaCard
  },
  data() {
    return {
      citas: []
    };
  },
  methods: {
    agregarCita(cita) {
      this.citas.push(cita);
    },
    eliminarCita(index) {
      this.citas.splice(index, 1);
    }
  }
};
</script>

<style>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}
h1 {
  text-align: center;
  color: #4955a8;
  margin-bottom: 20px;
}
.citas-container {
  margin-top: 20px;
}
</style>
