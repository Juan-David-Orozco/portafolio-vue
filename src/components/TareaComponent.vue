<template >
  <div>
    <div class="row mt-2 text-left" v-for="(task, index) in tasks" v-bind:key="index">
      <div class="col-1 h6">
        {{ index }}
      </div>
      <div class="col-4 h6">
        {{ task.nombre }}
      </div>
      <div class="col-1 h6">
        {{ task.esperado }}
      </div>
      <div class="col-4 h6">
        <avance-component
          v-bind:progreso='Number(task.avance)'
          v-bind:esperado='Number(task.esperado)'
        >
        </avance-component>
      </div>
      <div class="col-2 text-center mt-0 p-0">
        <span
          v-bind:id="'agregar'"
          v-bind:class="['mx-1', 'btn', 'btn-primary', agregar]"
          style="font-size: 8px"
          v-on:click="manejoClick($event)"
        ></span>
        <span
          v-bind:id="'eliminar-' + index"
          v-bind:class="['mx-1','btn', 'btn-primary', eliminar]"
          style="font-size: 8px"
          v-on:click="manejoClick($event)"
        ></span>
      </div>
    </div>
    <agregar-component
      v-bind:mostrar='mostrarAgregar'
      v-on:agregar='agregarTarea($event)'>
    </agregar-component>
  </div>
</template>

<script>
import AvanceComponent from "./AvanceComponent.vue";
import AgregarComponent from './AgregarComponent.vue'

export default {
  name: "tarea-component",
  data: function () {
    return {
      agregar: "fa fa-plus",
      eliminar: "fa fa-minus",
      mostrarAgregar: false,
      tasks: [
        { nombre: "Estudiar componentes en Vue", avance: 27, esperado: 45 },
        { nombre: "Estudiar las props de los componentes", avance: 49, esperado: 44, },
        { nombre: "Hacer actividades con los componentes", avance: 93, esperado: 100, },
        { nombre: "Hacer Ejercicios con los componentes", avance: 16, esperado: 35, },
      ],
    };
  },
  components: {
    AvanceComponent,
    AgregarComponent
  },
  methods: {
    manejoClick: function (e) {
      var btnId = e.target.id.split("-");
      if (btnId[0] === "eliminar") this.tasks.splice(btnId[1], 1);
      if (btnId[0] === 'agregar') this.mostrarAgregar = true;
    },
    agregarTarea: function (value) {
      this.tasks.push(value);
    }
  },
};
</script>



