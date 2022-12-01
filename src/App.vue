<template>

  <h1 class="title">Passarinho API</h1>

  <div class="container my-5">
    <CadastrarRecado @recadoCadastradoMsg="cadastrar" ></CadastrarRecado>
    <listar-recados :recadosProp="recados" ></listar-recados>
  </div>
</template>

<script>

import axios from "axios";

import CadastrarRecado from "./components/CadastrarRecado.vue";
import ListarRecados from "./components/ListarRecados.vue";

export default {
  name: "App",
  components: {
    CadastrarRecado,
    ListarRecados,
  },

  data(){
    return {
      url : "http://localhost:8082/recados",
      recados : []
    }
  },
  methods : {
      cadastrar(recadoTexto){
        
        let recado = {
          texto : recadoTexto
        }

        axios.post(this.url, recado).then((resposta)=>{
          console.log(resposta)
        }).catch((erro)=>{
          console.log(erro)
        });

      },

      buscarMensagens(){
     
        axios.get(this.url).then((resultado)=>{
            console.log(resultado['data'])
            this.recados = resultado['data']
        }).catch((erro) => {
            console.log(erro)
        });
     
      } //fim do método buscar
  },
  created() {
      this.buscarMensagens()
  },
  mounted(){
    setInterval(this.buscarMensagens, 3000)
  }
};
</script>

<style>
@import url("https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/css/bootstrap.min.css");

.title {
  text-align: center;
  margin: 45px;
}
</style>
