<template>
    <div class="overlay">
        <svg width="100%" height="100%">
            <circle class="overlay-bg" :class="{show:overlay}" />
            Sorry, your browser does not support inline SVG.
        </svg>
    </div>
</template>

<script>
    export default {
        name:"Overlay",
        props:["overlay"]
    }
</script>

<style scoped lang="scss">

    .overlay {
        width: 100%;
        height: 100%;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        position: absolute;
        pointer-events: none;
    }

    .overlay-bg{
        r: 0;
        cx: 100%;
        transition: ease-in-out 1s;
        pointer-events: all;
        fill: rgb(117, 163, 177);
    }

    .show {
        r:200%;
        fill: rgb(117, 163, 177);
    }
</style>