<template>
  <div class="progress">
    <div v-bind:class='["progress-bar",barColor]' role="progressbar" 
      v-bind:style='"width: "+progreso+"%"' aria-valuenow="25" 
      aria-valuemin="0" aria-valuemax="100">{{progreso}}%
    </div>
  </div>
</template>

<script>

  export default {
    name: 'avance-component',
    props: {
        progreso:Number,
        esperado:Number
    },
    data: function () {
      return {
        barColor:''
      }
    },
    beforeMount: function () {
      if (this.esperado>this.progreso+15)
        this.barColor='bg-danger'
      else if (this.esperado>this.progreso+5)
        this.barColor='bg-warning'
      else
        this.barColor='bg-info'
    },
    beforeUpdate: function () {
      if (this.esperado>this.progreso+15)
        this.barColor='bg-danger'
      else if (this.esperado>this.progreso+5)
        this.barColor='bg-warning'
      else
        this.barColor='bg-info'
    }
  }
</script>
