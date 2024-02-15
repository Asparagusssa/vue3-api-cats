<script setup lang="ts">
import { ref } from 'vue';

    const props = defineProps({
        toggle: Boolean
      })

const isLoading = ref(false)
const imgSrc = ref('')
const defaultImg = '/src/assets/img/kids.jpeg'
let err = ref(null)


async function fetchPic() {
  isLoading.value = true
  err.value = null

  try {
    const response = await fetch("https://api.thecatapi.com/v1/images/search")
    console.log(response)
    if(response.ok) {
      const data = await response.json()
      imgSrc.value = data[0].url
      console.log(imgSrc)
    }
  } catch (error) {
    error.value = error.message;
    console.log(error)
  } finally {
    isLoading.value = false
  }
}
</script>

<template>
    <main :class="{load: toggle}" class="catWrap">
      <p v-if="toggle">Is loading...</p>
      <p v-else-if="err">Ошибка: {{ err }}</p>
      <img class="catBox" v-else :src="imgSrc || defaultImg" alt="cat">
    </main>
    <button @click="fetchPic" :disabled="isLoading">Create Cat</button>

</template>

<style>

.catBox {
    max-width: 500px;
    max-height: 700px;
    box-shadow: 0 0 20px #000;
    border-radius: 15px;
  }
  
  
  .load {
    box-shadow: 0 0 20px #000;
    font-size: 2em;
  }
  
  .catWrap {

    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 1em;
    padding: 50px;
    border-radius: 15px;
    background-color: #fff;
  }

  button {
    padding: 0 10px;
    border-radius: 15px;
    font-size: 2em;
    border: 2px solid #04AA6D;
    color: #04AA6D;
    background-color: #fff;
    position: absolute;
    bottom: 1.5em;
  }
  
  button:hover {
    color: #fff;
    background-color: #04AA6D;
  }
  
  button:focus {
    outline: none;
    box-shadow: 0 0 0 4px #1cd08e;
  }

  button:disabled {
    background-color: gray;
    border: 2px solid gray;
  }

  @media (max-width: 610px) {
    img {
      height: 90%;
      width: 90%;
    }
    
    .catWrap {
      padding: 15px;
    }
  }

  @media (max-height: 800px) {
   
    .catWrap {
      max-height: 500px;
      overflow: hidden;
    }
  }
</style>
