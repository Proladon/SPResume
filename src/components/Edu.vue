<template>
    <div class="edu-wrapper section">
        <div class="edu-wrapper">
            <div class="edu-item-wrapper" v-for="item in edu" :key="item.school">
                <strong><p>{{ item.school }}</p></strong>
                <p> - {{ item.cert }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name:"Edu",
        props:["edu"],
        
    }
</script>

<style scoped lang="scss">

    .edu-item-wrapper{
        padding-top: 5px;
        padding-bottom: 5px;
    }
</style>