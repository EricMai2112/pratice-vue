<!-- Computed attributes allow to read only but user can use get, set to modify its value -->
<script setup>
    import { ref, reactive } from "vue"

    const isLoggedIn = ref(true)

    const btnLogin = () => {
        isLoggedIn.value = !isLoggedIn.value
    }

    const userStatus = ref("online")

    const btnChangeStatus = () => {
        if(userStatus.value === 'online'){
            userStatus.value ='away'
        }else if(userStatus.value === 'away'){
            userStatus.value = 'busy'
        }else if(userStatus.value === 'busy'){
            userStatus.value = 'online'
        }
    }

    const isVisibled = ref(true)

    const btnSetVisible = () => {
        isVisibled.value = !isVisibled.value
    }
</script>

<template>
    <div>
        <h1 v-if="isLoggedIn">Bạn đã đăng nhập</h1>
        <h1 v-else>Yêu cầu bạn đăng nhập</h1>    <br>
        <button @click="btnLogin">{{ isLoggedIn ? "Đăng xuất" : "Đăng nhập" }}</button>
    </div>
    <br>
    <div>
        <h1 v-if="userStatus ==='online'">Đang online</h1>
        <h1 v-else-if="userStatus ==='away'">Đang chờ</h1>
        <h1 v-else-if="userStatus ==='busy'">Đang vắng mặt</h1>
        <h1 v-else>Không trạng thái</h1><br>
        <button @click="btnChangeStatus">Thay đổi trạng thái</button>
    </div>
    <br>
    <div>
        <h1 v-show="isVisibled">Nội dung đang được hiển thị</h1>
        <button @click="btnSetVisible">{{ isVisibled ? "Ẩn" : "Hiện" }}</button>
    </div>
</template>

<style scoped>

</style>
