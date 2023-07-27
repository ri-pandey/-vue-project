<script setup>
import { computed, ref } from 'vue'

const x1 = ref(1)
const x2 = ref(2)

const doSomething = () => {
    // x1.value++
    computedValue.value = '3 4'
}

const computedValue = computed({
    get() {
        return x1.value + ' ' + x2.value
    },
    set(newValue) {
        [x1.value, x2.value] = newValue.split(' ')
    }
    // return (x1.value === 1 || x1.value === 2) ? "Equals 1 or 2" : "Does not equal 1 or 2"
})

</script>

<template>
    <div>x1: {{ x1 }}</div>
    <div>x2: {{ x2 }}</div>
    <!-- <div>computed value string: {{ computedValue }}</div> -->
    <!-- <div>date computed value : {{ dateComputedValue }}</div> -->
    <div @click="doSomething">Click me</div>
</template>