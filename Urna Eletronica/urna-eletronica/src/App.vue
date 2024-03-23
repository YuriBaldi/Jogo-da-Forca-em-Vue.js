<template>
  <div class="app">
    <div class="urna">

      <telaUrna
      :tela="tela"
      :quantidadeNumeros="quantidadeNumeros"
      :numeroVoto="numeroVoto"
      :candidato="candidato"

      />
      <tecladoUrna
      :adicionaNumero="adicionaNumero"
      :corrige="corrige"
      :confirmar="confirmar"
      />

    </div>

  </div>  
</template>

<script>

import '@/css/global.css';
import tecladoUrna from '@/components/tecladoUrna.vue';
import telaUrna from './components/telaUrna.vue';
export default {
  name: 'App',
  components: {
    tecladoUrna,
    telaUrna
    
  },

  methods:{
    adicionaNumero(numero){
      if(this.numeroVoto.length == this.quantidadeNumeros){
        return false;
      }
      this.numeroVoto += ''+ numero;

      this.verificarCandidato()
    },

    verificarCandidato(){
      //voto incompleto
      if (this.numeroVoto.length < this.quantidadeNumeros){
        return false;
      }
      if (this.candidatos[this.tela][this.numeroVoto]){
        this.candidato = this.candidatos[this.tela][this.numeroVoto];
        return true;
      }

      this.candidato = {
        nome:"Vladimir Putin",
        partido:"Mother Russia",
        imagem:'https://qph.cf2.quoracdn.net/main-qimg-824b288718f1f2a477a39b8aa1d63881-lq'
      }
    },

    limpar(){
      this.candidato={}
      this.numeroVoto=''
    },

    corrige(){
      this.limpar();
    },

    confirmar(){
      if (this.numeroVoto.length < this.quantidadeNumeros){
        return false;
      }
      return this.avancarTela();
    },

    avancarTela(){
      if(this.tela == 'prefeito'){
        this.tela ='vereador';
        this.quantidadeNumeros = 5;
        return this.limpar();
      }
      this.tela = 'fim';

      const instancia = this;

      setTimeout(() => {
        instancia.tela = 'prefeito';
        instancia.quantidadeNumeros = 2;
        return instancia.limpar();
      }, 3000);
        
      
    }
    
  },
  data(){
    return{
      tela:'prefeito',
      numeroVoto:'',
      quantidadeNumeros: 2,
      candidato:{},
      candidatos:{
            "prefeito":{
              "01":{
                "nome": "Ash",
                "partido": "Pokemon",
                "imagem": "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/ash.png"
              },
              "08":{
                "nome": "Vegeta",
                "partido": "Dragon Ball",
                "imagem": "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/vegeta.png"
              }
            },
            "vereador":{
                "01234":{
                  "nome": "Pikachu",
                  "partido": "Pokemon",
                  "imagem": "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/pikachu.png"
                },
                "08001":{
                  "nome": "Goku",
                  "partido": "Dragon Ball",
                  "imagem": "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/goku.png"
     }
  }
}

      
    }
  }
}
</script>

<style>
  #app {
    background-color: var(--background-color);
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;

  }

  .urna{
    width: 1000px;
    height: 500px;
    background-color: var(--ballot-box-background-color);
    padding: 30px;
    border-radius: 12px;
    display: flex;
    justify-content: space-between;
  }

</style>
