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
        v-if="etapa === 'jogo'"
        :letras="letras"
        :verificarLetra="verificarLetra"
        :jogar="jogar"
        />

        <FinalJogo
            v-if="etapa != 'jogo'"
            :etapa="etapa"
            :texto="etapa === 'ganhador' ? 'Parabens >:(' : 'Tadiiinho :('"
            :jogarnovamente="jogarnovamente"

        />
    
    </div>
</template>

<script>
import ForcaImage from './ForcaImage.vue'
import PalavraForca from './PalavraForca.vue'
import TecladoJogo from './TecladoJogo.vue'
import FinalJogo from './FinalJogo.vue'

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
        jogarnovamente: Function,
    },    
    methods:{
        
    },

    components:{
        ForcaImage,
        PalavraForca,
        TecladoJogo,
        FinalJogo,
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