<template>
    <div>Ma sélection : {{ selection.length }}
    <span v-if="nbrMoto">motos</span>
    <span v-else>moto</span>
    </div>
</template>

<script>
    export default {
        name: "MotoSelection",
        props:['selection'],
        computed: {
            nbrMoto(){
                if(this.selection.length > 1){
                    return true
                }
                return false
            }
        }
    }
</script>

<style scoped>

</style>
