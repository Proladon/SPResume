<template>
    <div class="design-skill">
        <!-- Software -->
        <div class="software" >
            <ul>
                <li v-for="sw in dataID.software" :key="sw">
                    {{sw}}
                </li>
            </ul>
        </div>
        
        <br><hr><br>
        <!-- Intro -->
        <div class="intro">
            <!-- EN -->
            <ul v-if="lang === 'EN'">
                <li v-for="it in dataID.EN.intro" :key="it">
                    {{it}}
                </li>
            </ul>
            
            <!-- CH -->
            <ul v-if="lang === 'CH'">
                <li v-for="it in dataID.CH.intro" :key="it">
                    {{it}}
                </li>
            </ul>

        </div>

    </div>
</template>

<script>
import skillID from '@/json/skillID.json'
    export default {
        name: "Design",
        props:["lang"],
        data(){
            return{
                dataID: skillID,
            }
        }
    }
</script>

<style scoped lang="scss">
    .design-skill {
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