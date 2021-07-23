<template>
  <NewToDoForm @onFormSubmit="AddNewtask" />
  <ToDoList 
  :todoTasks="taskList" 
  @deleteTask="deleteTodoTask"
  @completeTask="completeToDoTask" />
</template>

<script>
import NewToDoForm from './components/NewToDoForm'
import ToDoList from './components/ToDoList'
import { ref } from 'vue'

export default {
  components: {
    NewToDoForm,
    ToDoList
  },
  setup(){
    let taskList = ref([])

    const AddNewtask = (event) => {
      taskList.value.push({
          content: event,
          complete: false
        })
    }

    const completeToDoTask = (index) => {
      taskList.value[index].completed = !taskList.value[index].completed
    }

    const deleteTodoTask = (index) => {
      taskList.value.splice(index, 1)
    }

    return{
      AddNewtask,
      completeToDoTask,
      deleteTodoTask,
      taskList,
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
