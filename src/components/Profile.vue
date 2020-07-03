<template>
    <div class="profile section">
        <div class="avatar-wrapper">
            <img id="avatar" :src="avatar" alt="">
        </div>
        <div class="name-wrapper">
            <div class="name">{{ name }}</div>
            <div class="nick">{{ nick }}</div>
        </div>
        <!-- <div class="contact-wrapper">
            <div class="website"> <a :href="website" target="_blank">Personal Website</a> </div>
            <div class="mail"><a :href="`mailto:${mail}`">{{ mail }}</a> </div>
        </div> -->
    </div>
</template>

<script>
    export default {
        name: 'Profile',
        props:[
            "avatar",
            "name",
            "nick",
            "website",
            "mail"
        ]
    }
</script>

<style scoped lang="scss">
    .profile {
        /* border: springgreen solid 1px; */
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;

    }

    #avatar {
        width: 15vw;
        height: 15vw;
        border-radius: 15vw;
        /* max-height: 100px; */
        background-color: steelblue;
    }

    .name-wrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    .contact-wrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;
    }
</style>