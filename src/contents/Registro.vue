<template>
  <div class='container ml-5 pl-5 mt-2' v-if='!finRegistro'>

    <div id='titulo' class="row my-2">
      <h1>Registro de Usuario</h1>
    </div>

    <div class="row text-left">
      <div class='col-8 border rounded'>

        <div class="form-group">
          <label for="name" class="cols-sm-2 control-label">Nombre Completo</label>
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"><i class="fa fa-user fa" aria-hidden="true"></i></span>
            <input type="text" class="form-control" name="name" 
              id="name" placeholder='Nombre Completo'
              v-model='pdNombre'/>
          </div>
        </div>
     
        <div class="form-group">
          <label for="email" class="cols-sm-2 control-label">Correo Electrónico</label>
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"><i class="fa fa-envelope fa" aria-hidden="true"></i></span>
            <input type="text" class="form-control" name="email" 
              id="email" placeholder="Correo Electrónico"
              v-model="pdEmail"/>
          </div>
        </div>

        <div class="form-group">
          <label for="password" class="cols-sm-2 control-label">Contraseña</label>
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"><i class="fa fa-lock fa-lg" aria-hidden="true"></i></span>
            <input type="password" class="form-control" name="password" 
              id="password" placeholder="Ingrese la contraseña"
              v-model="pdClave"/>
          </div>
        </div>

        <div class="form-group">
          <label for="confirm" class="cols-sm-2 control-label">Confirmar Contraseña</label>
          <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info"><i class="fa fa-lock fa-lg" aria-hidden="true"></i></span>
            <input type="password" class="form-control" name="confirm" 
              id="confirm" placeholder="Confirme la contraseña"
              v-model="pdClaveConfirmar"/>
          </div>
        </div>

        <div class="form-group text-center">
          <button type="button" id='registrar'
            class="btn btn-primary btn-lg login-button"
            @click='manejoClick($event)'>Registro</button>
          <button type="button" id='cancelar'
            class="ml-2 btn btn-primary btn-lg login-button"
            @click='manejoClick($event)'>Cancelar</button>
        </div>

      </div>
    </div>

  </div>
  <div v-else class='container'>
    Registro exitoso.
    <a href='#' @click='irInicio'>Ir a inicio</a>
  </div>
</template>

<script>
export default {
  name:'registro-component',
  data: function () {
    return {
      pdNombre:'',
      pdEmail:'',
      pdClave:'',
      pdClaveConfirmar:'',
      finRegistro:false
    }
  },
  methods: {
    manejoClick: function (e) {
      if (e.target.id==='cancelar')
        this.$emit('cancelarRegistro')
      else{
        this.finRegistro=true
      }
    },
    irInicio: function () {
      this.$emit('irInicio',{nombre:this.pdNombre, email:this.pdEmail, clave:this.pdClave})
    }
  }
}
</script>
