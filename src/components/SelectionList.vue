<template>
    <div class="container w-4/5 mx-auto mt-4 ">
        <h1 class="text-lg font-bold">Mon comparatif</h1>

        <div v-if="selection.length == 0">
            <p>Aucune moto sélectionnée</p>
        </div>

        <div v-else>
            <div class="flex flex-wrap ">
            <div
                    v-for="moto in selection"
                    :key="moto.name"
                    class="border border-black my-4 p-2 "
            >
                <h3>{{ moto.name }} ({{ moto.cm3 }} cm3)</h3>
                <span>moto d'une puissance de {{moto.puissance}} chevaux et de {{moto.couple}} Nm de couple</span>
                <br>
                <span>{{ moto.prix }} €</span>
                <br>
                <span>moto {{moto.stock}}</span>
                <img :src="motoPhoto(moto.photo)" alt="" class="img">
            </div>
            </div>
        </div>

    </div>
</template>

<script>
    export default {
        name: "SelectionList",
        props:['selection'],
        methods: {
            motoPhoto(img){
                return require('@/assets/img/'+img)
            }
        }
    }
</script>

<style scoped>
.img {
    max-width: 80%;
}
    .border {
        max-width: 50%;
    }
</style>
