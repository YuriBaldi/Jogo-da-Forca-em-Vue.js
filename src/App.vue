<template>
  <div class="urna-eletronica">
    <a href="https://urna-eletronica-em-vue-js.vercel.app/" class="urna"> Ir para Urna Eletronica</a>
  </div>
  <div id="app">
    <h1>Jogo da Forca</h1>

    <section v-if = "tela === 'inicio'" id="inicio">
      
      <FormularioJogo v-if="etapa === 'palavra'"
        title="Defina a palavra"
        button="Próximo"
        :action="setPalavra"
      />
      <FormularioJogo v-if="etapa === 'dica'"
        title="Defina a dica"
        button="Iniciar o jogo"
        :action="setDica"
        
      />

    </section>

    <section v-if = "tela === 'jogo'" id="jogo">
      <JogoForca
        :erros="erros"
        :palavra="palavra"
        :dica="dica"
        :verificarLetra="verificarLetra"
        :etapa="etapa"
        :letras="letras"
        :jogar="jogar"
        :jogarnovamente="jogarnovamente"
      />
    </section>

  </div>
  
</template>

<script>
import './css/global.css'
import FormularioJogo from './components/FormularioJogo.vue';
import JogoForca from './components/JogoForca.vue';


export default {
  name: 'App',
  data () {
    return {
      tela: 'inicio',
      etapa: 'palavra',
      palavra: '',
      dica:'',
      erros: 0,
      letras: []
    }
  },
  components: {
    FormularioJogo,
    JogoForca
  },
  methods:{
    setPalavra: function (palavra) {
      this.palavra = palavra;
      this.etapa = 'dica';      
    },
    setDica: function (dica) {
      this.dica = dica;
      this.tela = 'jogo';
      this.etapa = 'jogo';      
    },

    verificarLetra: function(letra){
      return this.letras.find(item => item.toLowerCase() === letra.toLowerCase());
    },

    jogar: function(letra){
      this.letras.push(letra);
      this.verificarErros(letra);
    },
    
    verificarErros: function(letra){
      if(this.palavra.toLowerCase().indexOf(letra.toLowerCase()) >=0){
        return this.verificarAcertos();
      }
      this.erros++;

      if(this.erros===6){
        this.etapa = 'enforcado';
      }
    },

    verificarAcertos: function(){
      let letrasUnicas = [... new Set(this.palavra.split(''))];
      if (letrasUnicas.length === (this.letras.length - this.erros)){
        this.etapa = 'ganhador';
      }

    },

    jogarnovamente: function(){
      this.palavra='';
      this.dica='';
      this.erros=0;
      this.letras=[];
      this.tela='inicio';
      this.etapa='palavra';

    }

  }
}
</script>

<style>
#app {

  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.urna-eletronica{
  font-size: 15px;
  padding: 15px;
  margin-top: 15px;
  margin-left: 1100px;
  border: 2px solid #1abc9c;
  border-radius: 15px;
}

.urna{
  text-decoration: none;
  transition: 0.2s opacity;
}

.urna:hover{
  opacity: 0.8;
}
</style>
