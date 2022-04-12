<template>
  <div class='container'>
    <div class='row px-1 my-1'>
      <div class="col-md-4">
        Bienvenido al Sistema:
      </div>
      <div class="col-md-6 ">
        <b class="text-left">{{nombreUsuario}}</b>
      </div>
    </div>
    <div class="row">
      <div class="col">
        En el sistema puede acceder a las secciones Perfil y Actividades
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'inicio-component',
  props: ['nombreUsuario']
}
</script>

