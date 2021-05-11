<template>
  <div v-for="task in tasks" :key="task.id">
    <Task @delete-task="onDelete" @toggle-reminder="toggleReminder" :task="task"></Task>
  </div>
</template>

<script>
import Task from "./Task"
export default {
    name: 'Tasks',
    props:{
        tasks: Array,
    },
    components:{
        Task,
    },
    methods:{
        onDelete(id){
            this.$emit('delete-task',id);
        },
        toggleReminder(id){
            this.$emit('toggle-reminder',id);
        }
    }
}
</script>

<style>

</style>