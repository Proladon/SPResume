<template>
    <div class="awards-wrapper section">
        <div class="award-item-wrapper" v-for="item in awards" :key="item.years">
            <div > <strong class="years">{{ item.years }}</strong> </div>
            <div class="award-name">
                <ul>
                   <li v-for="award in item.award" :key="award">
                       {{ award }}
                    </li> 
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Awards",
        props:["awards"],
    }
</script>

<style scoped>
.award-item-wrapper{
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    padding-top: 10px;
    justify-content: space-between;
}

.years{
    font-size: 17px;
    text-align: center;
    
}

.award-name{
    width: 100%;
}

li{
    list-style: none;
}
</style>