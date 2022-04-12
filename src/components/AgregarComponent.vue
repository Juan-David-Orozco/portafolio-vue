<template>
  <div id='agregarStyle' class="row text-left mt-4" v-if='mostrar'>
    <div class="form-group col-5">
        <label for="tarea" class="cols-sm-2 control-label">Tarea</label>
        <div class="cols-sm-10">
            <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info">
                <i class="fa fa-tasks fa" aria-hidden="true"></i>
            </span>
            <input type="text" class="form-control" name="tarea" 
              id="tarea" placeholder="Descripción de la tarea"
              v-model='tarea'/>
            </div>
        </div>
    </div>
    <div class="form-group col-3">
        <label for="esperado" class="cols-sm-2 control-label">Avance Esperado</label>
        <div class="cols-sm-10">
            <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info">
                <i class="fa fa-percent fa" aria-hidden="true"></i>
            </span>
            <input type="text" class="form-control" name="esperado" 
              id="esperado" placeholder="Avance Esperado"
              v-model="esperado"/>
            </div>
        </div>
    </div>
    <div class="form-group col-3">
        <label for="progreso" class="cols-sm-2 control-label">Avance Real</label>
        <div class="cols-sm-10">
            <div class="input-group">
            <span class="pt-2 px-3 input-group-addon bg-info">
                <i class="fa fa-percent fa" aria-hidden="true"></i>
            </span>
            <input type="text" class="form-control" name="avance" 
              id="avance" placeholder="Avance Real"
              v-model="avance" />
            </div>
        </div>
    </div>
    <div class="form-group col-1">
        <label for="progreso" class="cols-sm-2 control-label"></label>
        <div class="cols-sm-10 mt-1">
            <span class="pt-2 px-3" v-on:click='manejoClick($event)'>
              <i class="fa fa-check-square" aria-hidden="true" id='agregar'></i>
            </span> 
            <span class="pt-2 px-3" v-on:click="manejoClick($event)">
              <i class="fa fa-ban" aria-hidden="true" id='cancelar'></i>
            </span> 
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'agregar-component',
  props: {activo: String, mostrar: Boolean},
  data: function () {
    return {
      tarea: '',
      esperado: '',
      avance: '',
      //mostrar: this.show
    }
  },
  methods: {
    manejoClick: function (e) {
      if (e.target.id==='agregar'){
        this.$emit('agregar',{nombre: this.tarea,esperado: this.esperado,avance: this.avance})
        this.tarea='';
        this.esperado='';
        this.avance='';
      }
      //else
      //  this.mostrar = false
    }
  }
}
</script>

<style>
  #agregarStyle {
    font-size: 14px;
  }
</style>
