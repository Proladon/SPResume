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
    @import url('https://fonts.googleapis.com/css2?family=Raleway:wght@500&display=swap');
    .header {
        width: 100%;
        height: 70px;
        box-sizing: border-box;
    }

    .deco-line {
        height: 100%;
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

    .slogan{
        font-size: 20px;
        font-family: 'Raleway', sans-serif;
    }
</style>