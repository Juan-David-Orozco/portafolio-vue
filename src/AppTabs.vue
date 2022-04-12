<template>
  <div id="app" class='m-2' >
    <nav>
      <div class="nav nav-tabs" id="nav-tab" role="tablist">
        <a v-bind:class='"nav-item nav-link "+mostrarInicio' id="inicio"
          data-toggle="tab" href="#nav-home" role="tab"
          aria-controls="nav-home" aria-selected="true"
          v-on:click='manejoClick($event)'>
          Inicio</a>
        <a v-bind:class='"nav-item nav-link "+mostrarPerfil' id="perfil"
          data-toggle="tab" href="#nav-profile" role="tab"
          aria-controls="nav-profile" aria-selected="false"
          v-on:click='manejoClick($event)'>
          Perfil</a>
        <a v-bind:class='"nav-item nav-link "+mostrarActividades' id="actividades"
          data-toggle="tab" href="#nav-contact" role="tab"
          aria-controls="nav-contact" aria-selected="false"
          v-on:click='manejoClick($event)'>
          Actividades</a>
      </div>
    </nav>
    <div class="tab-content" id="nav-tabContent">

      <div v-bind:class='"tab-pane fade show "+mostrarInicio' id="nav-home" role="tabpanel"
        aria-labelledby="nav-home-tab">
        <login-component
          v-if='!registro && !logon'
          v-on:eventoRegistro='activarRegistro'
          v-on:ingresoCorrecto='ingreso'
          v-bind:estadoLogon='logon'
          v-bind:datosPerfil='perfil'>
        </login-component>
        <registro-component
          v-if='registro && !logon'
          @cancelarRegistro='quitarRegistro'
          @irInicio='aInicio($event)'>
        </registro-component>
        <inicio-component
          v-if='logon'
          v-bind:nombreUsuario='perfil.nombre'>
        </inicio-component>
      </div>

      <div v-bind:class='"tab-pane fade show "+mostrarPerfil' id="nav-profile" role="tabpanel"
        aria-labelledby="nav-profile-tab">
        <perfil-componente
          v-bind:pNombre='perfil.nombre'
          v-bind:pEmail='perfil.email'
          v-bind:estadoLogon='logon'
          @actualizarPerfil='actualizarDatos($event)'>
        </perfil-componente>
      </div>

      <div v-bind:class='"tab-pane fade show "+mostrarActividades' id="nav-contact" role="tabpanel" 
        aria-labelledby="nav-contact-tab">Debe ingresar al Sistema.
      </div>

    </div>
  </div>
</template>

<script>
import LoginComponent from "./contents/Login.vue"
import RegistroComponent from "./contents/Registro.vue"
import InicioComponent from "./contents/Inicio.vue"
import PerfilComponente from "./contents/Perfil.vue"

export default {
  name: 'app',
  data: function () {
    return {
    logon: false,
    mostrarInicio: 'active',
    mostrarPerfil: '',
    mostrarActividades: '',
    registro:false,
    perfil : {nombre:'',email:'',pass:''}
  }},
  methods: {
    manejoClick: function (e) {
      if (e.target.id==='inicio'){
        this.mostrarInicio='active'
        this.mostrarPerfil=''
        this.mostrarActividades=''}
      else if (e.target.id==='perfil'){
        this.mostrarInicio=''
        this.mostrarPerfil='active'
        this.mostrarActividades=''}
      else{
        this.mostrarInicio=''
        this.mostrarPerfil=''
        this.mostrarActividades='active'}
    },
    activarRegistro: function (){
      this.registro=true
    },
    quitarRegistro: function (){
      this.registro=false
    },
    ingreso: function (){
      this.logon=true
      this.mostrarInicio='active'
      this.mostrarPerfil=''
      this.mostrarActividades=''
    },
    aInicio: function (e){
      this.perfil=e
      this.registro=false
    },
    actualizarDatos: function (e){
      this.perfil.nombre=e.nombre
      this.perfil.email=e.email
    }
  },
  components: {
    LoginComponent,
    RegistroComponent,
    InicioComponent,
    PerfilComponente
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
