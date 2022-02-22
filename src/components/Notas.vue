<template>
  <div id="componente">
    <h1>Resultado académico</h1>
    <div class="div">
      <label for="nombre">Introduzca su nombre</label>
      <input
        type="text"
        v-model="nombre"
        name="nombre"
        id="nombre"
        placeholder="Indique su nombre"
        required
      />
    </div>

    <div class="div">
      <label for="materia">Introduzca su materia</label>
      <input
        type="text"
        v-model="materia"
        name="materia"
        id="materia"
        placeholder="Indique su materia"
        required
      />
    </div>

    <div class="div">
      <label for="nota">Introduzca su nota</label>
      <input
        type="number"
        v-model="nota"
        name="nota"
        id="nota"
        placeholder="Indique su nota"
        required
      />
    </div>

    <div class="div">
      <button @click="calificacion">Enviar</button>
    </div>

    <div id="res">
      <p>{{ messageError }}</p>
      <p>{{ messageNombre }}</p>
      <p>{{ messageMateria }}</p>
      <p>{{ messageNota }}</p>
    </div>
  </div>
</template>
<style>
.div {
  margin-top: 20px;
}
.div label {
  margin-right: 20px;
}
</style>

<script>
export default {
  name: "Notas",
  data: () => ({
    nota: "",
    nombre: "",
    materia: "",
    messageNombre: "",
    messageMateria: "",
    messageNota: "",
    messageError: "",
  }),
  methods: {
    calificacion() {
      let nota = this.nota;
      let nombre = this.nombre;
      let materia = this.materia;

      if (nombre == 0 || materia == 0 || nota == 0) {
        this.messageError = "No ha completado los datos";
      } else if (!isNaN(nombre)) {
        this.messageNombre = "";
        this.messageError = "Escriba un nombre válido";
      } else if (!isNaN(materia)) {
        this.messageMateria = "";
        this.messageError = "Escriba una materia válida";
      } else if (nota < 0 || nota > 10 || isNaN(nota)) {
        this.messageMateria = "";
        this.messageError = "Escriba una nota válida entre el 0 y el 10";
      } else {
        this.messageError = "";
        this.messageNombre = this.nombre;
        this.messageMateria = this.materia;

        let result = Math.round(nota);
        if (result < 3 && result >= 0) {
          this.messageNota = "Muy deficiente";
        } else if (result < 5) {
          this.messageNota = "Insuficiente";
        } else if (result < 6) {
          this.messageNota = "Suficiente";
        } else if (result < 7) {
          this.messageNota = "Bien";
        } else if (result < 9) {
          this.messageNota = "Notable";
        } else if (result <= 10) {
          this.messageNota = "Sobresaliente";
        }
      }
    },
  },
};
</script>
