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
        :key='index'>
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
      this.Noticias=response.data.articles
    })
  }
}
</script>

<style lang="scss">
@import url(https://fonts.googleapis.com/css?family=Roboto:300);

$color-primary: #3498db;	
$color-secondary: #f1c40f;	

html, body{
  padding: 0;
  margin: 0;
  font-family: Roboto;
  background-color: #eee;
}

section{
  position: relative;
  width: 80%;
  background-color: #fff;  
  box-shadow: 0px 2px 10px rgba(0,0,0,.3);
  overflow: hidden;
  margin: 20px auto;
  border-radius: 2px;
}

.header{
  width: 100%;
  height: 15%;
  background-color: $color-primary;  
  overflow: hidden;
  
  .circle{
    position: relative;
    top: 20px;
    left: 120px;
    width: 50px;
    height: 50px;
    background-color: $color-secondary;    
    box-shadow: 0px 3px 3px rgba(0,0,0,.3);
    border-radius: 50%;
    z-index: 10;
  }
  
  h1{
    position: relative;
    top: 10px;
    left: 150px;
    font-size: 2.5em;
    color: #fff;
    border-bottom: 1px solid $color-secondary;
  }
}

.line{
  position: absolute;
  z-index: 0;
  top: 50px;
  left: 145px;
  height: calc(100% + 200px);
  width: 0px;
  border-right: 1px solid $color-secondary;
}

#content{
  width: 100%;
  height: 80%;
  overflow: hidden;
  padding-top: 20px;
  overflow-y: auto;
  overflow-x: hidden;
  
  &::-webkit-scrollbar {
    width: 6px;
    background-color: #EBEBEB;  
  }

  &::-webkit-scrollbar-thumb {
    background-color: #ccc; 
  }
  
  .object{
    width: 100%;
    &:after{
      content: "";
      display: block; 
      height: 0; 
      clear: both;
    }
    .date{
      float: left;
      width: 100px;
      height: 40px;
      margin: 20px;
      background-color: $color-secondary;
      color: #fff;
      border-radius: 10px;
      text-align: center;
      line-height: 1.9em;
      font-size: 1.1em;
    }
    .circle{
      position: relative;
      float: left;
      z-index: 10;
      margin: 30px 0 0 -5px;
      width: 20px;
      height: 20px;
      background-color: $color-primary;
      border-radius: 50%;
    }
    .context{
      float: left;
      color: #666;
      width: 60%;
      min-height: 40px;
      margin: 10px 0 0px 0px;
      padding: 10px 0px 0px 20px;
      line-height: 1.5em;
    }
  }
}
</style>
