<template>
  <div id="app">
    <div class='container border rounded mt-2'>
      <div class='row h4'>
        <div class='col-12'>
          Lista de tareas
        </div>
      </div>
      <div class='row h4 text-left'>
        <div class='col-1 text-left'>
          #
        </div>
        <div class='col-4'>
          Tareas
        </div>
        <div class='col-1'>
          Esp
        </div>
        <div class='col-4'>
          Avance
        </div>
        <div class='col-2 text-center'>
          Acción
        </div>
      </div>
      <tarea-component>
      </tarea-component>
    </div>
  </div>
</template>

<script>
import TareaComponent from './components/TareaComponent.vue'

export default {
  name: 'app',
  components: {
    TareaComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
