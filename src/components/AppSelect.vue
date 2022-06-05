<template>
    <form class="card card-w30" @submit.prevent="submitHandler">
        <div class="form-control">

            <label for="select">Тип блока</label>
            <select id="select" v-model="selected">
                <option v-for="option in options" :value="option.value">{{option.text}}</option>
            </select>
        </div>

        <div class="form-control">
            <label for="resumeValue">Значение</label>
            <textarea id="resumeValue" v-model="resumeValue" rows="3"></textarea>
        </div>
        <button class="btn primary" :disabled="disabled">Добавить</button>
    </form>
</template>

<script>
    export default {
        emits:['block-added'],
        props:['values'],
        data(){
            return {
                resumeValue: '',
                selected:'title',
                options: [
                    {text: 'Заголовок', value: 'title'},
                    {text: 'Подзаголовок', value: 'subTitle'},
                    {text: 'Аватар', value: 'avatar'},
                    {text: 'Текст', value: 'text'},

                ],
            }
        },
        methods:{
            submitHandler() {
                this.$emit('block-added', {
                    resumeValue : this.resumeValue,
                    selected: this.selected,
                    options: this.options

                })
                if(this.resumeValue !== '') {
                    this.values.push({
                        text: this.resumeValue,
                        type: this.selected
                    })
                }
                this.resumeValue = ''
            }
        },
        computed:{
            disabled(){
                return this.resumeValue.length < 1
            }
        }
    }
</script>

<style scoped>

</style>