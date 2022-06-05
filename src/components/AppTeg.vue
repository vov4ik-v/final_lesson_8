<template>
    <h1 v-if="type === 'title'">{{text}}</h1>
    <h2 v-else-if="type === 'subTitle'">{{text}}</h2>
    <p v-else-if="type === 'text'">{{text}}</p>
    <div class="avatar" v-else-if="type === 'avatar'">
        <img :src="text">
    </div>
</template>

<script>
    export default {
        props:{
            text:String,
            type:String

        }
    }
</script>

<style scoped>
    .avatar {
        display: flex;
        justify-content: center;
    }

    .avatar img {
        width: 150px;
        height: auto;
        border-radius: 50%;
    }
</style>