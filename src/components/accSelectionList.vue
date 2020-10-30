<template>
    <div class="container w-4/5 mx-auto mt-4 ">
        <h1 class="text-lg font-bold">Mon panier</h1>

        <div v-if="selection2.length == 0">
            <p>Aucun article sélectionné</p>
        </div>

        <div v-else>
            <div class="flex flex-wrap ">
                <div
                        v-for="acc in selection2"
                        :key="acc.name"
                        class="border border-black my-4 p-2 "
                >
                    <h3>{{ acc.name }}</h3>
                    <p>{{acc.prix}} €</p>

                    <img :src="accPhoto(acc.photo)" alt="" class="img">
                </div>

            </div>
            <p>Total : {{ total }} €</p>
        </div>

    </div>
</template>

<script>
    export default {
        name: "accSelectionList",
        props:['selection2'],
        methods: {
            accPhoto(img){
                return require('@/assets/img/'+img)
            }
        },
        computed: {
           total() {
                    var total = this.selection2.reduce(function(pV, currentValue){
                        return pV.prix + currentValue.prix;
                    });
                    return total;
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
