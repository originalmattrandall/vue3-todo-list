<template>
<h3>Add New Task</h3>
<form @submit.prevent="handleFormSubmit">
    <input v-model="userInput" type="text" />
    <button>Add New Task</button>
</form>
</template>

<script>
import { ref } from 'vue'

export default {
    setup (props, context) {
        const userInput = ref('')

        const handleFormSubmit = () => {
            if(!userInput.value) return
            context.emit('onFormSubmit', userInput.value)
            userInput.value = ''
        }

        return {
            userInput,
            handleFormSubmit,
        }
    }
}
</script>