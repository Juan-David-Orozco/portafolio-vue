<template>
  <div class='container'>
    <div class='row'>
      Bienvenido al Sistema  <b class='pl-2'> {{nombreUsuario}}</b>
    </div>
    <div class="row">
      En el sistema puede acceder a las secciones Perfil y Actividades
    </div>
  </div>
</template>

<script>
export default {
  name: 'inicio-component',
  props: ['nombreUsuario']
}
</script>

