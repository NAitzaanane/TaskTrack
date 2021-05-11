<template>
    <header>
        <h3>{{title}}</h3>
        <Button v-bind:text="showForm ? 'Cancel' : 'Add task'" v-bind:color="showForm ? 'brown' : 'green'" @btn-click="onClick"></Button>
    </header>
</template>
<script>
import Button from './Button'
export default {
    name: 'Header',
    props: {
        title: String,
        showForm: Boolean,
    },
    components:{
        Button,
    },
    methods: {
        onClick(){
            this.$emit('toggleForm');
        }
    }
}
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:ital,wght@100,100&display=swap');
    header{
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        align-items: center;
        margin-bottom: 20px;
    }
    h3{
        font-family: 'Roboto Mono', monospace;
    }
</style>