<template>
    <div class="profession section">
        <div v-for="pro in profession" :key="pro">
            {{ pro }}
        </div>
    </div>
</template>

<script>
    export default {
        name: "Profession",
        props: ["profession"]
    }
</script>

<style scoped>
    .profession {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }
</style>