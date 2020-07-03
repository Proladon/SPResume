<template>
  <div class="intro section">
      <p v-if="country==='EN'">
          {{dataIntro.EN}}
      </p>

      <p v-if="country==='CH'">
          {{dataIntro.CH}}
      </p>
  </div>
</template>

<script>
import intro from '@/json/intro.json'
export default {
    name:"Intro",
    props:["country"],
    data(){
        return{
            dataIntro: intro
        }
    }
}
</script>

<style scoped>
.intro{
    text-align: justify;
}
</style>