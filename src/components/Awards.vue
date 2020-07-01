<template>
    <div class="awards-wrapper section">
        <div class="award-item-wrapper" v-for="item in awards" :key="item.years">
            <div>{{ item.years }}</div>
            <div>
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
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}

li{
    list-style: none;
}
</style>