<template>
  <div class="app">
    <div class="urna">

      <tecladoUrna
      :adicionaNumero="adicionaNumero"
      />

      <telaUrna
      :tela="tela"
      :quantidadeNumeros="quantidadeNumeros"
      :numeroVoto="numeroVoto"

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
