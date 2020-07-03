<template>
    <div class="skill-wrapper section">
        <div 
            class="skill-item-wrapper" 
            v-for="skill in skills" 
            :key="skill.category" 
            @click="skillOverlay(skill.category)">
            
            <!-- Skill Category Name -->
            <div class="category" >
                <p>
                   <b>+ {{ skill.category }}</b>
                </p>
            </div>
            
            <!-- Lighting Circle -->
            <svg class="expand-btn" height="100%" width="10%">
                <circle  class="expand-circle" />
                <circle  class="expand-circle2" />
            </svg>

        </div>
    </div>
</template>

<script>
    export default {
        name:"Skill",
        props:[
            "skills"
        ],
        methods:{
            skillOverlay(typ){
                this.$emit('skillOverlay', typ)
            }
        }
    }
</script>

<style scoped lang="scss">

.skill-item-wrapper{
    display: flex;
    height: 30px;
    justify-content: space-between;
}

.category{
    height: 100%;
    display: flex;
    align-items: center;
    color: rgb(117, 163, 177);
}

.skill{
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 10px;
}


.expand-btn{
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
 
    .base-circle{
        cx: 50%;
        cy: 50%;
        r:3;
        fill: #B3C9CE;
        position: absolute;
    }

    .expand-circle{
        cx: 50%;
        cy: 50%;
        fill: #B3C9CE;
        position: absolute;
        animation-name: lighting;
        animation-duration: 2s;
        animation-iteration-count: infinite;
        animation-timing-function: ease-out;
    }
    
    .expand-circle2{
        cx: 50%;
        cy: 50%;
        fill: #DBDBDB;
        position: absolute;
        animation-name: lighting2;
        animation-duration: 2s;
        animation-iteration-count: infinite;
        animation-delay: .5s;
    }

    @keyframes lighting {
        0%{
            r:0;
            opacity: 100;
        }
        100%{
            r:10;
            opacity: 0;
        }
    }

    @keyframes lighting2 {
        0%{
            r:0;
            opacity: 100;
        }
        100%{
            r:10;
            opacity: 0;
        }
    }

}

hr{
    clear: both;
    
}
</style>