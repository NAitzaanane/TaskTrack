<template>
    <div @dblclick="$emit('toggle-reminder',task.id)" :class="['task',task.reminder ? 'reminder' : '']">
        <div class="text">
            <h6>{{task.text}}</h6>
            <small><p>{{task.day}}</p></small>
        </div>
        <i @click="onDelete(task.id)" class="fas fa-times"></i>     
    </div>
</template>

<script>
export default {
    name: 'Task',
    props:{
        task: Object,
    },
    methods: {
        onDelete(id){
            this.$emit('delete-task',id);
        }
    },
}
</script>

<style scoped>
    .task{
        display: flex;
        justify-content: space-between;
        background: lightblue;
        margin: 10px;
        border-radius: 5px;
        padding: 2%;
        transition: 0.2s;
        font-family: 'Roboto Mono', monospace;
    }
    .task:hover{
        filter: brightness(90%);
    }
    .text{
        text-align: left;
    }
    .fas{
        color: rosybrown;
        transition: 0.4s;
    }
    .fas:hover{
        color: red;
        cursor: pointer;
    }
    .reminder{
        border-left: solid 6px green;
    }
</style>