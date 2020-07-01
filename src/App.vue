<template>
    <div id="app">
        <div id="lang" @click="changeLang">EN / CH</div>
        <div class="page-wrapper">

            <hooper id="main-hooper">
                <slide>
                    <Header 
                        :slogan1="lang.slogan.slogan1" 
                        :slogan2="lang.slogan.slogan2" />

                    <Profile 
                        :avatar="lang.avatar" 
                        :name="lang.name" 
                        :nick="lang.nick" 
                        :mail="lang.mail"
                        :website="lang.website" />

                    <Profession :profession="lang.profession" />

                    <EduSkill :edu="lang.edu" @skillOverlay="overlaySkill" />

                    <Awards :awards="lang.awards" />
                </slide>

                <slide>
                    <EduSkill :edu="lang.edu" />
                </slide>
            </hooper>

            <div class="footer">
                <p><span>{{ page }}</span> / 2</p>
                ← Slide →
            </div>
            <!-- Overlay -->

            <div class="overlay" >
                <svg width="100%" height="100%">
                    <circle class="overlay-bg" :class="{show:overlay}"/>
                    Sorry, your browser does not support inline SVG.
                    <circle class="overlay-btn" :class="{btn_show:overlay}" @click="overlay=false"/>
                </svg>
                
            </div>
        </div>

        <div id="lang">EN / CH</div>
    </div>
</template>

<script>
    import {
        Hooper,
        Slide
    } from 'hooper';
    import 'hooper/dist/hooper.css';
    import resumeCH from './json/resumeCH.json'
    import resumeEN from './json/resumeEN.json'
    import Header from './components/Header.vue'
    import Profile from './components/Profile.vue'
    import Profession from './components/Profession.vue'
    import EduSkill from './components/EduSkill.vue'
    import Awards from './components/Awards.vue'
    export default {
        name: 'App',
        components: {
            Hooper,
            Slide,
            Header,
            Profile,
            Profession,
            EduSkill,
            Awards,
        },
        data() {
            return {
                overlay: false,
                page: 1,
                CH: resumeCH,
                EN: resumeEN,
                country: 'CH',
                lang: Object,
            }
        },
        methods: {
            changeLang() {
                if (this.country === 'EN') {
                    this.country = 'CH'
                    this.lang = this.CH
                } else if (this.country === 'CH') {
                    this.country = 'EN'
                    this.lang = this.EN
                }
            },
            overlaySkill(text) {
                console.log(text)
                this.overlay = true
            }
        },
        mounted() {
            this.lang = this.CH
        }
    }
</script>

<style lang="scss">
    * {
        margin: 0;
        padding: 0;
        font-size: 12px;
        
    }

    body {
        background-color: #B3C9CE;
    }

    #app,
    body,
    html {
        width: 100%;
        height: 100%;
    }

    .section {
        padding-top: 15px;
        padding-bottom: 15px;
    }

    #lang {
        text-align: center;
        margin: 15px;
    }

    .page-wrapper {
        width: 87%;
        margin: 0 auto;
        background-color: #DBDBDB;
        box-shadow: 30px 30px 60px 1px rgba(23, 35, 47, 50);
        padding: 20px;
        box-sizing: border-box;
        position: relative;
    }

    .footer {
        text-align: center;
    }

    #main-hooper {
        height: 100%;
        outline: none;
    }

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
        r:1000;
        fill: rgb(117, 163, 177);
        border-radius: 0 30px 0 0;
    }

    .overlay-btn{
        cx: 95%;
        cy:3.5%;
        r: 0;
        fill: rgb(39, 55, 70);
        cursor: pointer; 
        pointer-events: all;
        transition: ease-in-out 1s;
    }

    .btn_show{
        r: 10;
    }

</style>