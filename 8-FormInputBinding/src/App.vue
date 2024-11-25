<!-- Computed attributes allow to read only but user can use get, set to modify its value -->
<script setup>
    import { ref } from 'vue';

    const textArea = ref('Hello')

    const text = ref('')

    const sports = ref([])
    
    const genders = ref()

    const classes = ref()
</script>

<template>
    <div>
        <h1>Please type your messages below:</h1>
        <textarea name="" id="" v-model="textArea"></textarea><br>
        <p>{{ textArea }}</p>

        <input v-model="text" placeholder="Type your message here">
        <p>Message: {{ text }}</p> 

        <h1>Your favourite sports: {{ sports }}</h1>
        <input type="checkbox" v-model="sports" id="sport1" value="Football">
        <label for="sport1">Football</label>
        <input type="checkbox" v-model="sports" id="sport2" value="Basketball">
        <label for="sport2">Basketball</label>
        <input type="checkbox" v-model="sports" id="sport3" value="Volleyball">
        <label for="sport3">Volleyball</label>

        <h1>Gender: {{ genders }}</h1>
        <input type="radio" v-model="genders" id="genderFemale" value="0">
        <label for="genderFemale">Female</label>
        <input type="radio" v-model="genders" id="genderMale" value="1">
        <label for="genderMale">Male</label>

        <h1>Choose class that you want to join: {{ classes }}</h1>
        <select v-model="classes">
            <option disabled>please choose class</option>
            <option :value="{Type: 'Food', Name: 'Chicken'}">A</option>
            <option :value="{Type: 'Drink', Name: 'Cocacola'}">B</option>
            <option :value="{Type: 'Dessert', Name: 'Cake'}">C</option>
        </select>
    </div>
</template>

<style scoped>

</style>
