<template>
  <div v-if='estadoLogon'>
    Perfil
  </div>
  <div v-else>
    Debe ingresar al Sistema.
  </div>
</template>

<script>
export default {
  name:'perfil-componente',
}
</script>

