<template>
    <div class="jogo">
        
        <ForcaImage
        :erros="erros"
        />

        <PalavraForca
        :palavra="palavra"
        :dica="dica"
        :verificarLetra="verificarLetra"
        :etapa="etapa"
        />

        <TecladoJogo
        :letras="letras"
        :verificarLetra="verificarLetra"
        :jogar="jogar"

        />
    
    </div>
</template>

<script>
import ForcaImage from './ForcaImage.vue'
import PalavraForca from './PalavraForca.vue'
import TecladoJogo from './TecladoJogo.vue'

export default {
    name: 'JogoForca',
    props:{
        erros: Number,
        palavra: String,
        dica: String,
        verificarLetra: Function,
        etapa: String,
        letras: Array,
        jogar: Function,
    },    
    methods:{
        
    },

    components:{
        ForcaImage,
        PalavraForca,
        TecladoJogo,
    }

}
</script>

<style>

.jogo{

    display: flex;
    width: 100%;
    flex-direction: column;
    align-items: center;
    text-align: center;
}

</style>