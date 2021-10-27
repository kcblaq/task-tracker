<template>
    <div>
        <form @submit="onSubmit" class="add-form">
            <div class="form-control"> 
                <label> Task </label>
            <input type="text" v-model="text" name="text" placeholder="Add Task" />
            </div>
            <div class="form-control"> 
                <label> Day and time </label>
            <input type="date" v-model="day" name="day" placeholder="Add Day and time" />
            </div>
            <div class="form-control form-control-check"> 
                <label> Set Reminder 
            <input type="checkbox" v-model="reminder" name="reminder" />
            </label>
            </div>

            
            

            <input type="submit" value="Add Task" class="btn"/>
        </form>

    </div>
</template>
<script>
export default {
    name: "AddTask",

    data() {
        return {
            text: '',
            reminder: false,
            day: ''
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault();
            if(!this.text){
              return  alert("Add a task before submitting")
            } 
            const newTask = {
                text: this.text,
                day: this.day,
                reminder: this.reminder,
            }
            this.text = '', 
            this.day = '',
            this.reminder =  false

            this.$emit('add-task', newTask)
        }
    }
}
</script>

<style scoped>
.form-control input{
    width: 100%;
    height: 2rem;
}
</style>