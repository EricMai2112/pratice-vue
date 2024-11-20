<!-- Computed attributes allow to read only but user can use get, set to modify its value -->
<script setup>
    import { computed, ref } from 'vue';

    const firstName = ref('Nguyen Van')
    const lastName = ref('A')

    const fullName = computed({
        get(){
            return firstName.value + ' ' + lastName.value
        },

        set(newValue){
            [firstName.value, lastName.value] = newValue.split(',')
        }
    })

    const change = () => {
        fullName.value = 'Nguyen Van, B'
    }
</script>

<template>
    <div>
        <p>Full Name: {{ fullName }}</p>
        <p>First Name: {{ firstName }}</p>
        <p>Last Name: {{ lastName }}</p>
        <button @click="change"> Change Name </button>
    </div>
</template>

<style scoped>

</style>
