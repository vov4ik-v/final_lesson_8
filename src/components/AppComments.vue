<template>
    <div class="card" v-if="comments.length">
            <h2>Комментарии</h2>
            <ul class="list" v-for="comment in comments" :key="comment.id">
                <li class="list-item">
                    <div>
                        <p><strong>{{comment.nickname}}</strong></p>
                        <small>{{comment.body}}</small>
                    </div>
                </li>
            </ul>
        </div>
        <p v-else>
            <button class="btn primary" @click="$emit('load-comments')">Загрузить коментарии</button>
        </p>

</template>

<script>
    export default {
        emits:['load-comments'],
        data(){

        },
        props:[
            'comments'
        ],

    }

</script>

<style scoped>

</style>