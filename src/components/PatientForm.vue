<template>
  <form @submit.prevent="enviarFormulario">
    <div class="form-group">
      <label :class="{ 'error-label': !paciente }">Paciente</label>
      <input v-model="paciente" type="text" class="form-input" />
    </div>

    <div class="form-group">
      <label :class="{ 'error-label': !fecha }">Fecha</label>
      <input v-model="fecha" type="date" class="form-input" />
    </div>

    <div class="form-group">
      <label :class="{ 'error-label': !hora }">Hora</label>
      <input v-model="hora" type="time" class="form-input" />
    </div>

    <div class="form-group">
      <label :class="{ 'error-label': !gravedad }">Gravedad</label>
      <select v-model="gravedad" class="form-input">
        <option disabled value="">Selecciona una gravedad</option>
        <option value="Baja">Baja</option>
        <option value="Media">Media</option>
        <option value="Alta">Alta</option>
      </select>
    </div>

    <div class="form-group">
      <label :class="{ 'error-label': !motivo }">Motivo</label>
      <input v-model="motivo" type="text" class="form-input" />
    </div>

    <button
      :disabled="!paciente || !fecha || !hora || !gravedad || !motivo"
      class="submit-btn"
    >
      Agregar
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      paciente: '',
      fecha: '',
      hora: '',
      gravedad: '',
      motivo: ''
    };
  },
  methods: {
    enviarFormulario() {
      const cita = {
        paciente: this.paciente,
        fecha: this.fecha,
        hora: this.hora,
        gravedad: this.gravedad,
        motivo: this.motivo
      };
      this.$emit('add-cita', cita);
      this.limpiarFormulario();
    },
    limpiarFormulario() {
      this.paciente = '';
      this.fecha = '';
      this.hora = '';
      this.gravedad = '';
      this.motivo = '';
    }
  }
};
</script>

<style scoped>
.form-group {
  margin-bottom: 15px;
}
.form-input {
  width: 100%;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
}
.error-label {
  color: red;
}
.submit-btn {
  background-color: #4955a8;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  font-weight: bold;
}
.submit-btn:disabled {
  background-color: #ccc;
}
</style>
