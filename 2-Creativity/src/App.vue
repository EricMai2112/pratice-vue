<script setup>
    import {reactive, ref} from 'vue';

    const dem = ref(0)

    const increaseCount =  () => dem.value++;

    const object = reactive({
        count: 1,
        user: {
            age: 30
        },
        array: [1, 2, 3]
    })
    
    const Change = () => {
        object.count++
        object.user.age++
        object.array.push(4)
    }
</script>

<template>
    <button @click="increaseCount">Click to increase count: {{ dem }}</button><br>

    <button @click = "Change">Click to change</button><br>
    <p>Count: {{ object.count }}</p><br>
    <p>User Age: {{ object.user.age }}</p><br>
    <p>Array: {{ object.array }}</p>
</template>

<style scoped>

</style>
