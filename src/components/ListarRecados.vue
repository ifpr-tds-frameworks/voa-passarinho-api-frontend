<template>
  <div class="listar-recados">

    <div v-for="(recado, index) in recadosProp" :key="index"  class="recado">
  
      <span>{{recado.data}}</span>
      <p>{{recado.texto}}</p>
  
    </div>

  </div>
</template>

<script>
export default {

  name : 'ListarRecados',
  props :{
    recadosProp : Array
  }

}
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Merriweather:ital,wght@1,300&display=swap');

    .listar-recados {
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between; 
    }

    .recado {

        width: 250px;
        margin-bottom: 25px;
        padding: 10px;
        border: 1px solid #ced4da;
        border-radius: 5px;
        text-align: center;

        font-family: 'Merriweather', serif;
    }

</style>