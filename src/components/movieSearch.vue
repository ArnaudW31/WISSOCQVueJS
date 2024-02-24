<template>
    <div style="margin:auto; border: 2px black solid;width: 200px;text-align: center;">
        <p>Nom du film :</p>
        <input v-model="recherche" type="text" style="background-color: paleturquoise;">
    </div>
</template>

<script>
export default {
    name: 'MovieSearch',
    data(){
        return{
            recherche : ""
        }
    },
    watch:{
        recherche(val){
            this.$emit('searchMovieEmit', val);
        }
    }
}
</script>