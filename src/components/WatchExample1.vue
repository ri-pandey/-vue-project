<script setup>
import { ref, watch } from 'vue'

const question = ref('')
const answer = ref('Questions usually contain a question mark')

watch(question, async (newQuestion, oldQuestion) => {
    if (newQuestion.indexOf('?') > -1) {
        answer.value = 'Thinking...'
        try {
            const res = await getMockedAsyncResponse()
            answer.value = res
        } catch (err) {
            answer.value = "Encountered error reaching server: " + err
        }
    }
})

const getMockedAsyncResponse = () => {
    return new Promise((resolve) => {
        const options = ["Yes", "No"]
        setTimeout(() => resolve(options[Math.floor(Math.random() * options.length)]), 1000)
    })
}
</script>

<template>
    <p>
        Ask a question:
        <input v-model="question" />
    </p>
    <p>{{ answer }}</p>
</template>