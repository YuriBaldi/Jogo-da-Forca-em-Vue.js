<template>
    <div class="final">
        <div :class="`final-texto ${etapa}`">
            {{ texto }}
        </div>
        
        <button class="final-botao"
        @click="jogarnovamente">Jogar Novamente</button>

    </div>
        
</template>

<script>

export default {
    name: 'FinalJogo',
    props:{
        etapa: String,
        texto: String,
        jogarnovamente: Function,
        
        
    }, 
    data(){
        return{

        }
    },   
    methods:{
        
    }

}
</script>

<style>

.final-texto{
    margin: 20px 0px;
    font-size: 24px;
    font-weight: bold;

}

.final-texto.enforcado {
    color: var(--color-text-error);
}

.final-texto.ganhador {
    color: #2ecc71;
}

</style>