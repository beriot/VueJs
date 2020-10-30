<template>
    <button class="bg-teal-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
        {{ text }}
    </button>
</template>

<script>
    export default {
        name: "BaseButton",
        props: ['text']
    }
</script>

<style scoped>

</style>
