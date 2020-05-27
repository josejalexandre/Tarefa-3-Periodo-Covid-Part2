<template>
  <div id="ferramentas">
      <select v-model="caixaSel">
          <option></option>
          <option v-for="(caixa,index) in caixinhas" :key="index" :value="index">
              {{ caixa.titulo }}
          </option>
      </select>

        <div id="paleta">
            <div class="cor" :style="cor" v-for="(cor, index) in cores" :key="index" @click="alteraCor(cor)"></div>
            <input id="caixaTexto" type="text" placeholder="Novo nome" v-model="titulo">
            <button id="botao" @click="alterarTexto">OK</button>
        </div>


  </div>
</template>

<script>
export default {
    name: "Ferramentas",
    computed: {
        caixinhas(){
            return this.$store.state.caixinhas
        }
    },
    data: function(){
        return{
            cores: ['background: gray', 'background: green', 'background: yellow'],
            caixaSel: '',
            titulo: ''
        
        }
    },
    methods: {
        alteraCor: function(cor) {
            this.$store.commit('alteraCor', {
                cor: cor,
                caixa: this.caixaSel
            })
        },
        alterarTexto: function(){
            this.$store.commit('alterouTexto', {
                titulo: this.titulo,
                caixa: this.caixaSel
            })
        }
    }
}
</script>

<style>
    #ferramentas{
        width: 380px;
        height: 200px;
        border: 1px solid #FFF;
        margin: 5px auto 0 auto;
        padding: 10px;
    }
    #ferramentas select{
        width: 325px;
        height: 25px;
        margin: 5px 0 15px 0;
    }
    #paleta{
        width: 380px;
        height: 160px;
        display:flex;
        flex-wrap: wrap;
    }
    .cor{   
        width: 50px;
        height: 50px;
        border: 1px solid #FFF;
        margin: 10px 15px 0px 45px;
    }
    #caixaTexto{
        width: 325px;
        height: 25px;
    }
    #botao{
        width: 40px;
        height: 30px;
        background: green;
        border: none;
        color: white;
    }
</style>