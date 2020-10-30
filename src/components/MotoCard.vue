<template>
    <div class="border border-green-900 m-2 p-2 rounded "
         :class="isStockClass">
        <h3 class="text-lg font-bold">{{ motoName }} ({{ moto.cm3 }}cm3)</h3>
        <p>{{ moto.prix }} €</p>

        <base-button text="Sélectionner" @click="addToSelection"></base-button>
    </div>
</template>

<script>
    import BaseButton from "./global/BaseButton";
    export default {
        name: "MotoCard",
        components: {BaseButton},
        props: ['moto'],

        computed: {
            motoName(){
                if ( this.moto.name.split('.').length > 1){
                    return this.moto.name.split('.')[1]
                }
                return this.moto.name;
            },
            motoStock() {
                if(this.moto.stock == "non disponible"){
                    return true
                }
                return false
            },

            isStockClass(){
                return {
                    'bg-gray-600': this.motoStock,
                    'bg-gray-400': !this.motoStock
                }
            },

        },
        methods: {
            addToSelection() {
                this.$emit('add-moto', this.moto)
            }
        }
    }
</script>

<style scoped>

</style>
