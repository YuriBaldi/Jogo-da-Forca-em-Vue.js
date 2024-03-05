<template>
    <div class="Teclado">

        <button
            class="teclado-botao"
            v-for="(letra, key) in 'abcdefghijklmnopqrstuvwxyz'"
            :key="key"
            :disabled="verificarLetra(letra)"
            @click="jogar(letra)">
            {{ letra }}
        </button>

    </div>
        
</template>

<script>

export default {
    name: 'TecladoJogo',
    props:{
        letras: Array,
        verificarLetra: Function,
        jogar: Function
        
    },    
    methods:{
        
    }

}
</script>

<style>

.teclado{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width:80%;
    margin-top: 20px;
}

.teclado-botao{
    margin: 5px;
    text-transform: uppercase;
}

</style>