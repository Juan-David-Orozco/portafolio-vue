<template>
  <div class="container ml-5 pl-5 mt-2" v-if="estadoLogon">
    <div id="titulo" class="row my-2">
      <h1>Perfil del Usuario</h1>
    </div>

    <div class="row text-left">
      <div class="col-8 border rounded">
        <div class="form-group">
          <label for="name" class="cols-sm-2 control-label"
            >Nombre Completo</label
          >
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"
              ><i class="fa fa-user fa" aria-hidden="true"></i
            ></span>
            <input
              type="text"
              class="form-control"
              name="name"
              id="nombre"
              placeholder="Nombre Completo"
              v-bind:value="pNombre"
            />
          </div>
        </div>

        <div class="form-group">
          <label for="email" class="cols-sm-2 control-label"
            >Correo Electrónico</label
          >
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"
              ><i class="fa fa-envelope fa" aria-hidden="true"></i
            ></span>
            <input
              type="text"
              class="form-control"
              name="email"
              id="correo"
              placeholder="Correo Electrónico"
              v-bind:value="pEmail"
            />
          </div>
        </div>

        <div class="form-group text-center">
          <button
            type="button"
            id="actualizar"
            class="btn btn-primary btn-lg login-button"
            @click="manejoClick($event)"
          >
            Actualizar
          </button>
        </div>
      </div>
    </div>
  </div>
  <div v-else class="container">Debe ingresar al Sistema.</div>
</template>

<script>
export default {
  name: "perfil-componente",
  props: {
    estadoLogon: Boolean,
    pNombre: String,
    pEmail: String,
  },
  data: function () {
    return {
      pdNombre: "",
      pdEmail: "",
      finRegistro: false,
    };
  },
  methods: {
    manejoClick: function (e) {
      if (e.target.id === "actualizar") {
        this.$emit("actualizarPerfil", {
          nombre: document.getElementById("nombre").value,
          email: document.getElementById("correo").value,
        });
      } else {
        this.finRegistro = true;
      }
    },
  },
};
</script>

