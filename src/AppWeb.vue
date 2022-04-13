<template>
  <section>
    <div class="header">
      <h1> Noticias </h1>
    </div>
    <div id="content">
      
      <noticia-componente
        v-for='(noticia,index) in Noticias' 
        :fecha='noticia.publishedAt' 
        :titulo='noticia.title'
        :imagen='noticia.urlToImage'
        :detalle='noticia.content'
        :url='noticia.url'
        :fuente='noticia.source.name'
        :key='index'
      >
      </noticia-componente>
    
    </div>
  </section>
</template>

<script>
import NoticiaComponente from './webservices/Noticia.vue'
import axios from 'axios'

export default {
  name: 'app',
  components: {
    NoticiaComponente
  },
  data: function () {
    return { Noticias: [] }
  },
  created: function (){
    const apiKey='c68e380658bf4a0aa6cec24ce0c5e221';
    const pais='co';
    axios.defaults.headers.common['Authorization'] = apiKey;
    axios.get('https://newsapi.org/v2/top-headlines?country='+pais)
    //axios.get('https://newsapi.org/v2/top-headlines?country='+pais,{headers:{'X-Api-Key':apiKey}})
    .then(response => {
      if (response.status===200)
        this.Noticias=response.data.articles
      else{
        this.Noticias=[{
          publishedAt:Date.now(),
          title:'Error en la carga de datos',
          urlToImage:'http://icons.iconarchive.com/icons/aha-soft/software/128/cancel-icon.png',
          content:'Se presentó un error al tratar de cargar las noticias en el sistema.',
          source:{name:'Sistema Interno'}
        }]
      }
    })
    .catch(() => {
      this.Noticias=[{
          publishedAt:Date.now(),
          title:'Error en la carga de datos',
          urlToImage:'http://icons.iconarchive.com/icons/aha-soft/software/128/cancel-icon.png',
          content:'Se presentó un error al tratar de cargar las noticias en el sistema.',
          source:{name:'Sistema Interno'}
        }]
    })
  }
}
</script>

