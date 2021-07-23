<template>
    <div class="todo-items">
        <h3>Get These Done</h3>
        <ul>
            <li :key="todo.content + index" v-for="(todo, index) in todoItems">
                <span :class="{ completed: todo.completed }">{{todo.content}}</span>
                <button @click="completeTask(index)">Complete</button>
                <button @click="deleteTask(index)">Delete</button>
            </li>
        </ul>
    </div>
</template>

<script>
import { ref } from 'vue'

export default {
    props: {
        todoTasks: {
            type: Array
        },
    },
    setup (props, context) {
        const todoItems = ref(props.todoTasks)

        const completeTask = (index) => {
            context.emit('completeTask', index)
        }

        const deleteTask = (index) => {
            context.emit('deleteTask', index)
        }

        return {
            todoItems,
            completeTask,
            deleteTask
        }
    }
}
</script>

<style scoped>
    .completed{
        text-decoration: line-through;
    }
</style>