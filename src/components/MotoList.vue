<template>
    <h1>Liste des motos de la marque {{ motoData.name}}</h1>
    <p>Ajoutez des motos au comparatif pour découvrire les différentes caractéristiques !!</p>
    <moto-selection :selection="selection"></moto-selection>
    <moto-card v-for="(moto, index) in motoData.motos" :key="index" :moto="moto" @add-moto="addMotoToSelection"></moto-card>

    <h1>Liste des articles de la marque {{ motoData.name}}</h1>
    <p>Ajoutez des articles au panié</p>
    <acc-selection :selection="selection2"></acc-selection>
    <acc-card v-for="(acc, index) in motoData.articles" :key="index" :acc="acc" @add-acc="addAccToSelection"></acc-card>
</template>

<script>
    import motoData from '../assets/data/moto.json'
    import MotoCard from "./MotoCard";
    import MotoSelection from "./MotoSelection";
    import accCard from "./accCard";
    import AccSelection from "./accSelection";


    export default {
        name: "MotoList",
        components: {
            AccSelection,
            MotoCard,
            MotoSelection,
            accCard,

        },
        data() {
            return {
                motoData : motoData,
                selection: [],
                selection2: []
            }
        },
        methods: {
            addMotoToSelection(moto) {
                this.selection.push(moto)
                this.$emit('update-selection', moto)
            },
            addAccToSelection(acc) {
                this.selection2.push(acc)
                this.$emit('update-selection2', acc)
            }
        }
    }
</script>

<style scoped>

</style>
