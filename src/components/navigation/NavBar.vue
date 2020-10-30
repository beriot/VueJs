<template>
    <div class="bg-teal-700 p-2 text-center">
        <a v-for="(link,index) in navigation" :key="index" href="#" @click="selectComponent(link.component)"> {{ link.name }} </a>
    </div>
</template>

<script>
    export default {
        name: "NavBar",
        data(){
            return{
                navigation: [
                    { name: "Toutes les motos | ", component: "moto-list"},
                    { name: "Mon comparatif | ", component: "selection-list"},
                    { name: "Panier", component: "acc-selection-list"}
                ]
            }
        },
        methods: {
            selectComponent(comp) {
                this.$emit('change-component', comp)
            }
        }
    }
</script>

<style scoped>

</style>
