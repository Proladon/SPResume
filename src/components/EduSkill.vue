<template>
    <div class="edu_skill-wrapper section">
        <!-- EDU -->
        <div class="edu-wrapper">
            <div class="item-wrapper" v-for="item in edu" :key="item.school">
                <p>{{ item.school }}</p>
                <p>{{ item.cert }}</p>
            </div>
        </div>

        <!-- Sskill -->
        <div class="skill-wrapper">
            <p @click="skillOverlay('IDS')">工業設計 技能</p>
            <p>程式設計 技能</p>
            <p>2D/3D創作 技能</p>
            <p>影音多媒體 技能</p>
        </div>
    </div>
</template>

<script>
    export default {
        name:"Edu_Skill",
        props:["edu"],
        methods:{
            skillOverlay(typ){
                this.$emit('skillOverlay', typ)
            }
        }
    }
</script>

<style scoped lang="scss">
    .edu_skill-wrapper {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }
</style>