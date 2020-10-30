<template>
    <div class="border border-green-900 m-2 p-2 rounded "
         :class="isStockClass">
        <h3 class="text-lg font-bold">{{ accName }}</h3>
        <p>{{ acc.prix }} €</p>

        <base-button text="Sélectionner" @click="addToSelection"></base-button>
    </div>
</template>

<script>
    import BaseButton from "./global/BaseButton";
    export default {
        name: "accCard",
        components: {BaseButton},
        props: ['acc'],

        computed: {
            accName(){
                if ( this.acc.name.split('.').length > 1){
                    return this.acc.name.split('.')[1]
                }
                return this.acc.name;
            },
            accStock() {
                if(this.acc.stock == "out"){
                    return true
                }
                return false
            },

            isStockClass(){
                return {
                    'bg-gray-600': this.accStock,
                    'bg-gray-400': !this.accStock
                }
            },

        },
        methods: {
            addToSelection() {
                this.$emit('add-acc', this.acc)
            }
        }
    }
</script>

<style scoped>

</style>
