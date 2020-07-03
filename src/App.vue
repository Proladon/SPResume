<template>
    <div id="app">
        <div id="lang" @click="changeLang">EN / CH</div>
        <div class="page-wrapper">

            <hooper id="main-hooper" :wheelControl="false">
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

                <slide>
                    <img src="./assets/qr-code.svg" width="50%">
                </slide>
            </hooper>

            <div class="footer section">
                <p><span>{{ page }}</span> / 2</p>
                ← Slide →
            </div>

            <!-- Overlay -->
            <Overlay :overlay="overlay" @overlaySync="syncOverlayVal" />
            
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
    import Overlay from './components/Overlay.vue'
    
    // import Design from './components/skill/Design.vue'
    // import Programming from './components/skill/Programming.vue'
    import SkillOverlay from './components/skill/SkillOverlay.vue'

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
            Overlay,
            // Design,
            // Programming,
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
            overlaySkill(text) {
                console.log(text)
                this.overlay = true
                this.skillShow = text
            },
            syncOverlayVal(val){
                this.overlay = val
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

</style>