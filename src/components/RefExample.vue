<script setup>
import { onMounted, ref } from 'vue'

const list = ref(['first', 'second', 'third'])

const itemRefs = ref([])

onMounted(() => {
    // input.value.focus()
    console.log(itemRefs.value)
})
</script>

<template>
    <ul>
        <li v-for="item in list" ref="itemRefs">{{ item }}</li>
    </ul>
    <!-- <input ref="input"/> -->
</template>