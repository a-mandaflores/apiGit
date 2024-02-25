<template>
  <div class="procurar">
    <input v-model="inputValue" type="text">
    <button @click="enviarDados">serch</button>
  </div>
  <div v-if="naoEncontrado" class="naoEncontrado">Não foi possivel localizar, tente novamente</div>
  <ApiDados :loginApi="inputValue" :verificar="procurar" @verificado="mudandoProcurar" @naoEncontrado="renderizarNotFound" />
</template>

<script>
import ApiDados from "./ApiDados.vue"
export default {
  name: 'ApiGit',
  emits: ['verificado'],
  components: {
    ApiDados
  },
  data(){
    return{   
      inputValue: '',
      procurar: false,
      naoEncontrado: false
    }

  },
  methods:{
    enviarDados(){
      this.procurar = true
    },
    mudandoProcurar(verificado){
      this.inputValue = ''
      this.procurar = verificado
    },
    renderizarNotFound(){
      this.naoEncontrado = true
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

.procurar{
  display: flex;
  justify-content: center;
  width: 900px;

  padding: 2rem;
  background-color: #333;

  input, button{
    border: none;
  }

  input{ 
    padding: .3rem .1rem;
    width: 13rem;
    border-radius: 5px 0 0 5px;
    &:focus{
      border: none;
    }
  }

  button{
    cursor:pointer;
    padding: .3rem 1rem;
    border-radius: 0 5px 5px 0;

    
  }
 
}

.git{
  color: #333;
  cursor: pointer;
  display: flex;
  border-radius: 5px;
  margin: .5rem 1rem;
  background-color: #CCCCCC;

  img{
  margin: 1rem;
  width: 80px;
  height: 80px;
  border-radius: 50%;
  overflow: hidden;
  }
  .resultado{
  display: flex;
  flex-direction: column;

  h1{
    font-size: .9rem;
  }
  .nome{
    margin-top: .7rem;

  }
  .login{
    font-weight: 300;
    font-size: .6rem;
  }

  .bio{
    margin-top: 1rem;
    font-size: .8rem;
  }

  }

}




</style>
