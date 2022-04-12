<template>
  <div id='login'>
    <div v-if='!logon'>
      Login
    </div>
    <div v-else>
      <div class='text-center'><h2>Bienvenido al Sistema</h2></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'login-component',
}
</script>

