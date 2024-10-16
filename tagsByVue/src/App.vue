<script setup>
    import { ref, computed } from 'vue';
    
    const languages = ref(["Javascript", "HTML", "CSS"]);
    
    const data = ref('');

    function handleAdd(){       
        isShowPopup.value = true;
    }

    function clickToAdd(){
        languages.value.push(data.value);
        data.value = '';
        isShowPopup.value = false;
    }

    function clickToCancel(){
        isShowPopup.value = false;
        data.value = '';
    }

    const remainingTags = computed(()=>{
        return `${languages.value.length} tags are remaining`;
    })

    function handleDelete(index){
        languages.value.splice(index, 1);
    }

    function handleButtonRemoveAll(){
        languages.value = [];
    }

    const isShowPopup = ref(false);

    function handleClick(){
        isShowPopup.value = true;
    }

    function handleClosePopup(){
        isShowPopup.value = false;
    }

  </script>

<template>
    <div class="container">
<!-- popup -->
<div class="popup-container" v-if="isShowPopup ===true" @click="handleClosePopup">
      <div class="popup-main" @click.stop="handleClickMain">
        <div class="popup-header">
          <span class="popup-close__btn">x</span>
        </div>

        <div class="popup-content">
          Are you sure to add this item?
        </div>
        <div class="popup-action">
          <button @click="clickToCancel">Cancel</button>
          <button @click="clickToAdd">Confirm</button>
        </div>
      </div>
     </div>


        <div class="title">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 256 256"><g fill="none" stroke="currentColor" stroke-width="16"><path stroke-linecap="round" stroke-linejoin="round" d="M 240.04121,64.000608 240,208 c -0.005,15.99988 -16.04134,32 -32,32 H 48 C 31.958138,240 15.996182,223.99988 16,208 l 0.04199,-175.999258"/><path stroke-linecap="round" stroke-linejoin="round" d="m 224,48 c 8.83652,8e-6 15.99999,7.163485 16,16"/><path d="m 144.04154,48.000675 h 79.99974"/><path stroke-linecap="round" stroke-linejoin="round" d="m 106.38483,16.000772 a 15.999945,15.999945 0 0 1 13.85635,7.999985"/><path stroke-linecap="round" stroke-linejoin="round" d="M 144.04154,48.000675 A 15.999945,15.999945 0 0 1 130.18519,40.00069"/><path stroke-linecap="round" stroke-linejoin="round" d="M 144.04154,48.000675 A 15.999945,15.999945 0 0 0 130.18519,56.00066"/><path d="m 120.24118,24.000757 9.94401,15.999933"/><path stroke-linecap="round" stroke-linejoin="round" d="m 106.3848,80.000579 a 15.999945,15.999945 0 0 0 13.85638,-7.999986"/><path d="M 120.24118,72.000593 130.18519,56.00066"/><path stroke-linecap="round" stroke-linejoin="round" d="m 16,80 90.38472,5.79e-4"/><path stroke-linecap="round" stroke-linejoin="round" d="m 32.041967,16.000772 c -8.836533,3e-6 -15.999992,7.167628 -15.999978,16.004161"/><path stroke-linecap="round" stroke-linejoin="round" d="M 32.041967,16.000772 H 106.38498"/></g></svg>
            <h2>Tags</h2>
        </div>
            <p>Press enter or add a comma after each tag</p>
        <div class="list">
            <div class="item" v-for="(language, index) in languages">
                <p>{{ language }}</p>
                <svg @click="handleDelete(index)" xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32"><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 23L23 9m0 14L9 9"/></svg>
            </div>
            <input type="text" name="" id="txtLanguages" placeholder="Mới..." v-model="data" @keyup.enter="handleAdd">
        </div>
        <div class="footer">
            <p class="countLanguages">{{ remainingTags }}</p>
            <button @click="handleButtonRemoveAll" class="btnRemoveAll">Remove All</button>
        </div>
    </div>
</template>

<style scoped>
    body{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    .container{
        padding: 20px;
        background-color: white;
        color: black;
        border-radius: 10px;
    }

    .container p{
        margin-top: 10px;
    }

    .title{
        display: flex;
        gap: 15px;
    }

    .title h2{
        font-weight: bold;
    }

    .list{
        border: 1px solid #878686  ;
        margin: 20px 0px;
        display: flex;
        flex-wrap: wrap;
    }
    
    .item{
        margin: 10px;
        border: 1px solid #e8e8e8;
        width: fit-content;
        padding: 4px;
        background-color: #f2f2f2;
        display: flex;
        align-items: center;
        border-radius: 4px;
        gap: 7px;
    }

    .item svg{
        height: 25px;
        width: 25px;
        cursor: pointer;
    }

    .footer{
        display: flex;
        justify-content: space-between;
        gap: 10px;
        margin-top: 20px;
    }

    .btnRemoveAll{
        padding: 10px;
        border: none;
        background-color: #5173e9;
        color: white;
        border-radius: 4px;
        cursor: pointer;
    }
    #txtLanguages{
        border: none;
        width: 60px;
        background-color: white;
        padding: 4px;
        margin: 10px;
    }

    #txtLanguages:focus{
        outline: none;
    }

    /* popup */
.popup-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #7a7a7a;
  display: flex;
  justify-content: center;
  align-items: center;
}
.popup-main {
  background-color: #fff;
  padding: 20px;
  border-radius: 12px;
  display: grid;
  gap: 20px;
}

.popup-header {
  display: flex;
  justify-content: flex-end;
}

.popup-action {
  display: flex;
  gap: 12px;
}

.popup-action button {
  flex: 1;
}
</style>