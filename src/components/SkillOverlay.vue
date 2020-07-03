<template>
    <div class="skill-overlay">
        <!-- Software -->
        <div class="software" >
            <ul>
                <li v-for="sw in data.software" :key="sw">
                    {{sw}}
                </li>
            </ul>
        </div>
        
        <br><hr><br>
        <!-- Intro -->
        <div class="intro">
            <!-- EN -->
            <ul v-if="lang === 'EN'">
                <li v-for="it in data.EN.intro" :key="it">
                    {{it}}
                </li>
            </ul>
            
            <!-- CH -->
            <ul v-if="lang === 'CH'">
                <li v-for="it in data.CH.intro" :key="it">
                    {{it}}
                </li>
            </ul>

        </div>

    </div>
</template>

<script>
import skillID from '@/json/skillID.json'
import skillCD from '@/json/skillCoding.json'
import skillArt from '@/json/skillArt.json'
import skillMedia from '@/json/skillMedia.json'
    export default {
        name: "SkillOverlay",
        props:["category", "lang"],
        data(){
            return{
                data: Object,
            }
        },
        created(){
            if (this.category === 'Industrial Design' | this.category === '工業設計')
            {
                this.data = skillID
            }
            else if (this.category === 'Programming' | this.category === '程式設計')
            {
                this.data = skillCD
            }
            else if (this.category === '2D/3D Art' | this.category === '2D/3D 創作')
            {
                this.data = skillArt
            }
            else if (this.category === 'Media Design' | this.category === '多媒體設計')
            {
                this.data = skillMedia
            }
        }

    }
</script>

<style scoped lang="scss">
    .skill-overlay {
        width: 100%;
        height: 100%;
        top: 5%;
        bottom: 0;
        left: 0;
        right: 0;
        opacity: 100;
        position: absolute;
        pointer-events: none;
        padding: 15%;
        box-sizing: border-box;
        animation-name: showskill;
        animation-duration: 2s;
    }

    @keyframes showskill{
        0%{opacity: 0;}
        30%{opacity: 0;}
        100%{opacity: 100;}
    }

    .software li{
        list-style: none;
    }

    .intro ul{
        margin-left: 15px;

        li{
            padding-top: 10px;
        }
    }

    
</style>