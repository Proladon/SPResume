<template>
    <div id="app">
        <div id="lang" @click="changeLang">
            <span :class="{highlight:country==='EN'}">EN</span> / <span :class="{highlight:country==='CH'}">CH</span>
        </div>
        <div class="page-wrapper">

            <hooper id="main-hooper" :wheelControl="false" @slide="chpage">
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

                    <Edu :edu="lang.edu"  />
                    <Skill :skills="lang.skills" @skillOverlay="overlaySkill" />

                    <Awards :awards="lang.awards" />
                </slide>

                <!-- Page 2 -->
                <slide>
                    <Intro :country="country" />
                    <Links />
                </slide>

            </hooper>

            <!-- Footer -->
            <div class="footer section">
                <p><span>{{ page }}</span> / 2</p>
                <p style="letter-spacing: 5px;">← Slide →</p>
            </div>

            <!-- Overlay -->
            <Overlay :overlay="overlay" />
            <svg id="overlay-cls-btn">
                <circle id="cls-btn" :class="{cls_btn_show:overlay}" @click="closeOverlay"/>
                <text x="35%" y="65%" id="cls-btn-text" :class="{cls_btn_text_show:overlay}">--</text>
            </svg>

            <!-- If Skill -->
            <SkillOverlay 
                v-if="skillShow == 'Industrial Design' | skillShow == '工業設計'" 
                :lang="country" 
                :category="skillShow" 
            />

            <SkillOverlay 
                v-if="skillShow == 'Programming' | skillShow == '程式設計'" 
                :lang="country" 
                :category="skillShow" 
            />

            <SkillOverlay 
                v-if="skillShow == '2D/3D Art' | skillShow == '2D/3D 創作'" 
                :lang="country" 
                :category="skillShow" 
            />

            <SkillOverlay 
                v-if="skillShow == 'Media Design' | skillShow == '多媒體設計'" 
                :lang="country" 
                :category="skillShow" 
            />

        </div>

        <div id="lang">(。・ω・。)</div>
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
    import Edu from './components/Edu.vue'
    import Skill from './components/Skill.vue'
    import Awards from './components/Awards.vue'
    import Intro from './components/Intro.vue'
    import Links from './components/Links.vue'

    import Overlay from './components/Overlay.vue'
    import SkillOverlay from './components/SkillOverlay.vue'

    export default {
        name: 'App',
        components: {
            Hooper,
            Slide,
            Header,
            Profile,
            Profession,
            Edu,
            Skill,
            Awards,
            Intro,
            Links,
            Overlay,
            SkillOverlay,
        },
        data() {
            return {
                overlay: false,
                page: 1,
                CH: resumeCH,
                EN: resumeEN,
                country: 'EN',
                lang: Object,
                skillShow: String,
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
            chpage(payload){
                this.page = payload.currentSlide +1
            },
            overlaySkill(text) {
                this.overlay = true
                this.skillShow = text
            },
            closeOverlay(){
                this.overlay = false
                this.skillShow = ''
            }

        },
        created() {
            this.lang = this.EN
        }
    }
</script>

<style lang="scss">
    @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@300&display=swap');
    * {
        margin: 0;
        padding: 0;
        font-size: 12px;
        font-family: 'Noto Sans TC', sans-serif;
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
        color: gray;
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

    .highlight{
        // color: rgb(39, 146, 165);
        color: white;
    }

    #overlay-cls-btn{
        width: 25px;
        height: 25px;
        position: absolute;
        top: 15px;
        right: 15px;
    }

    #cls-btn{
        cx: 50%;
        cy: 50%;
        r: 0;
        fill: rgb(39, 55, 70);
        transition: ease-in-out 1s;
    }

    .cls_btn_show{
        r: 10 !important;
    }

    #cls-btn-text{
        opacity: 0;
        transform: translateX(-20px);
        pointer-events: none;
        transition: ease-in-out 1s;
        transition-delay: .5s;
    }
    .cls_btn_text_show{
        transform: translateX(0) !important;
        opacity: 100 !important;
        stroke: white;
        fill: white;
    }
</style>