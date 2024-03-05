<template>
    <div class="Forca">
        <img :src="`https://raw.githubusercontent.com/william-costa/wdev-hangman-game-resources/master/images/hangman/${erros}.svg`">
    </div>
</template>

<script>

export default {
    name: 'ForcaImage',
    props:{
        erros: Number
        
    },    
    methods:{
        
    }

}
</script>

<style>

.Forca img{
    height: 150px;
}

</style>