
<template>
  <div class="corpo">
    <h1 class="centralizado">{{ titulo }}</h1>
 

  <ul class="lista-fotos">
    <li class="lista-fotos-item" v-for="foto of fotos">

      <div class="painel">
        <h2 class="painel-titulo">
          {{ foto.titulo }}
        </h2>
        <div class="painel-conteudo">
          <img :src="foto.url" :alt="foto.titulo"/>
        </div>
      </div>

    </li>
  </ul>

  </div>


</template>

<script>
export default {

  data(){

    return {
      titulo: 'Do.ogs',
      fotos: []
    }
  },

  created() {


    this.$http.get('http://localhost:3000/v1/fotos')
      .then(res => res.json())
      .then(fotos => this.fotos = fotos, err => console.log(err));

  }

 
}
</script>

<style>
.corpo{
  font-family: Helvetica, sans-serif;
  width: 96%;
  margin: 0 auto;
  }

  .centralizado{
    text-align: center;  
  }

  .lista-fotos{
    list-style: none;
  }
  .lista-fotos-item{
    display: inline-block
    ;
  }
</style>
