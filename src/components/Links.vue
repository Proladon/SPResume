<template>
    <div class="links section">
        <div class="qrcode-wrapper" v-for="link in linksData" :key="link.name">
            <img :src="link.qrcode">
            <div class="link-intro">
                <strong><p>{{link.name}}</p></strong>
                <strong><a :href="link.url" target="_blank">Direct Link</a></strong>
                
                <p class="intro-text">
                    {{link.introEN}}
                </p>
                <p class="intro-text">
                    {{link.introCH}}
                </p>
            </div>
        </div>
    </div>
</template>

<script>
import links from '@/json/links.json'
    export default {
        name: "Links",
        data(){
            return{
                linksData: links
            }
        }
    }
</script>

<style scoped>
    .qrcode-wrapper{
        display: flex;
        padding-bottom: 20px;
    }

    .link-intro{
        box-sizing: border-box;
        padding-left: 20px;
    }

    img{
        max-width: 25vw;
    }

    .intro-text{
        padding-top: 2px;
        word-break: break-all;
    }

    a{
        color: rgb(117, 163, 177);
        /* color: rgb(65, 148, 168); */
    }

</style>