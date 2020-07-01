<template>
    <div class="header section">
        <div class="deco-line"></div>
        <div class="slogan-wrapper">
            <div class="slogan">{{ slogan1 }}</div>
            <div class="slogan">{{ slogan2 }}</div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Header',
        props:["slogan1", "slogan2"]
    }
</script>

<style scoped lang="scss">
    .header {
        width: 100%;
        height: 15%;
        box-sizing: border-box;
    }

    .deco-line {
        height: 2em;
        width: 2px;
        background-color: #B3C9CE;
        float: left;
    }

    .slogan-wrapper {
        height: 100%;
        float: right;
        display: flex;
        flex-direction: column;
        justify-content: space-between;

        text-align: right;
        font-family: consolas;
    }
</style>