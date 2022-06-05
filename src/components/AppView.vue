<template>
    <div class="card card-w70">
        <div v-if="values.length>0" v-for="text in values" :key="values.text">
            <app-teg :type="text.type" :text="text.text"></app-teg>
        </div>
        <div v-else>
            <h3>Добавьте первый блок, чтобы увидеть результат</h3>
        </div>
    </div>
</template>

<script>
    import AppTeg from "./AppTeg";
    export default {
        emits:[],
        props:['values'],
        components:{
            AppTeg
        }

    }
</script>

<style scoped>

</style>
