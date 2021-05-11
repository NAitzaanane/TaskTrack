<template>
  <Header @toggleForm="toggleForm" title="Task tracker" :showForm="showAddTask"></Header>
  <AddTask v-show="showAddTask" @new-task="addTask"></AddTask>
  <Tasks @delete-task="deleteTask" :tasks="tasks" @toggle-reminder="toggleReminder"></Tasks>
</template>

<script>
import Header from '../components/Header'
import Tasks from '../components/Tasks'
import AddTask from '../components/AddTask'
import Footer from '../components/Footer'
export default {
  name: 'Home',
  components: {
    Header,
    Tasks,
    AddTask,
    Footer,
  },
  data(){
    return{
      tasks: [],
      showAddTask: null,
    }
  },
  async created(){
    this.tasks = await this.fetchTasks();
  },
  methods:{
    async deleteTask(id){
      if(confirm('Delete task ?')){
        const res = await fetch(`api/tasks/${id}`,{
          method: 'DELETE',
        });
        res.status === 200 ? this.tasks = this.tasks.filter((task) => task.id !== id) : alert('Error deleting task');
      }
    },
    async toggleReminder(id){
      const taskToToggle = await this.fetchTask(id);
      const upd = {...taskToToggle,reminder:!taskToToggle.reminder};
      const res = await fetch(`api/tasks/${id}`,{
        method: 'PUT',
        headers: {
          'content-type': 'application/json',
        },
        body: JSON.stringify(upd) 
      });
      const data = await res.json();
      let myTask = this.tasks.find((task) => task.id === id);
      myTask.reminder = !myTask.reminder;
    },
    async addTask(newTask){
      const res = await fetch('api/tasks',{
        method: 'POST',
        headers: {
          'content-type': 'application/json',
        },
        body: JSON.stringify(newTask),
      });
      this.tasks = [...this.tasks,newTask];
    },
    toggleForm(){
      this.showAddTask = !this.showAddTask;
    },
    async fetchTasks(){
      const res = await fetch('api/tasks');
      const data = await res.json();
      return data;
    },
    async fetchTask(id){
      const res = await fetch(`api/tasks/${id}`);
      const data = await res.json();
      return data;
    }
  }
}
</script>

<style>

</style>