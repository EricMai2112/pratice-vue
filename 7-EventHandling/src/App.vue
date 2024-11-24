<!-- Computed attributes allow to read only but user can use get, set to modify its value -->
<script setup>
    import { ref } from 'vue';

    const count = ref(0);

    const sayContent = (content) => {
        alert('Nội dung là: ' + content);
    } 

    const sayHi1 = () => {
        alert('say hi 1')
    }

    const sayHi2 = () => {
        alert('say hi 2')
    }
</script>

<template>
    <div>
        <h1>Event Handling</h1> 
        <button v-on:click="count++">Thêm</button>
        <p>{{ count }}</p>

        <button @click="sayContent('VueJS')">Say</button>
 <br>
        <button @click="sayHi1">
            button1
            <button @click.stop="sayHi2">
                <!-- Use click.stop or click.self to prevent bubble event -->
                button2
            </button>
        </button>
    </div>
</template>

<style scoped>

</style>
