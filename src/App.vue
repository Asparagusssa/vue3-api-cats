<script setup lang="ts">
import MainHeader from './components/MainHeader.vue';
import CatBox from './components/CatBox.vue';
</script>

<template>
  <div class="wrapper">

    <MainHeader />
    <CatBox/>
    
  </div>
  
</template>

<style scoped>
.wrapper {
  display: flex;
  justify-content:start;
  align-items: center;
  flex-direction: column;
  background-color: wheat;
  height: 100vh;
  
}


</style>
