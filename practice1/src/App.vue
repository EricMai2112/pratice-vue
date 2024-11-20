<script setup>
    const message = 'Hello Everyone'
    const rawHTML = '<h1 style ="Color: red;">Hi everyone</h1>'

    const btnID = 'btn-id'

    const btnClass = 'btn-id-1'

    const isButtonDisabled = false

    const objectContainer = {
        id: 'buttonID1',
        class: 'buttonClass1',
        style: {
            color: 'red',
            backgroundColor: 'blue'
        }
    }

    const number = 5
    
    const listID = 'a, b, c, d, e, f, g, h, i, j, k'

    const attribute = 'href'

    const url = 'https://github.com/EricMai2112'
</script>

<template>
    <h1>Syntax</h1>
    <h2>Message: {{ message }}</h2>

    <p v-html="rawHTML"></p>

    <button :id="btnID" :class="btnClass" :disabled="isButtonDisabled">{{ isButtonDisabled ? 'disabled' : 'Click here!' }}</button> <br>

    <button v-bind="objectContainer">Press me!</button>

    <button :id="listID.split(',').join('-')">Test</button>

    <p>Number: {{ number * 2 }}</p>

    <a v-bind:[attribute] ="url" >My github</a>
</template>

<style scoped>

</style>
