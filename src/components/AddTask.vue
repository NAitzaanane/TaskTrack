<template>
  <form @submit="onSubmit" class="form-group frm">
      <input v-model="text" type="text" placeholder="Task text" class="form-control"><br>
      <input v-model="day" type="text" placeholder="day & time" class="form-control"><br>
      <div class="form-check">
        <input v-model="reminder" class="form-check-input" type="checkbox" value="" id="flexCheckDefault">
        <label class="form-check-label" for="flexCheckDefault">
            Set reminder
        </label>
      </div><br>
      <input type="submit" class="btn btn-dark" value="Save task">
  </form>
</template>

<script>
export default {
    name: 'AddTask',
    data(){
        return{
            text: '',
            day: '',
            reminder: false,
        }
    },
    methods: {
        onSubmit(e){
            e.preventDefault();
            if(!this.text){
                alert('Add a task first');
                return
            }
            const newTask = {
                // id: Math.floor(Math.random()*100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder,
            }
            this.text = '';
            this.day = '';
            this.reminder = false;
            this.$emit('new-task',newTask);
        }
    }
}
</script>

<style>

</style>