<template>
    <div>Ma sélection : {{ selection.length }}
        <span v-if="nbrAcc">Articles</span>
        <span v-else>article</span>
    </div>
</template>

<script>
    export default {
        name: "accSelection",
        props:['selection'],
        computed: {
            nbrAcc(){
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
