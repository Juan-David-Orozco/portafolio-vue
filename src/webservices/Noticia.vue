<template>
  <div class="object my-3">
    <div class="card">
      <div class="row text-center mt-2">
        <div class="col-12"><img class='imagen rounded' :src='imagen ? imagen:imagenDefecto' style="width:75%"/></div>
      </div>
      <div class="card-body">
        <b class="my-2">{{titulo}}<br/>{{fecha}}</b>
        <p>{{detalle}} Fuente: {{fuente}}</p>
        <a v-if='url' :href='url' target='_blank' >Leer detalle...</a>
      </div>
    </div>

  </div>
  
</template>

<script>
//import moment from 'moment'

export default {
  name: 'noticia-componente',
  props: ['fecha','imagen','titulo','detalle','url','fuente'],
  data: function () {
    return {
      imagenDefecto: "http://icons.iconarchive.com/icons/pelfusion/long-shadow-ios7/128/News-icon.png"}
  },
  /* 
  filters: {
    formatoFecha: function (fecha) {
     moment.locale(navigator.language);
     return moment(fecha).format('dddd, D MMMM hh:mm:ss')
    }
  }
  */
}
</script>
