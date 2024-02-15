<script setup lang="ts">
import { ref } from 'vue';

const blur = ref(0)




</script>

<template>
    <footer class="options">
        <button>обычный</button>
        <button>милый</button>
    
        <div class="filters">
          <button>mono</button>
          <button>negative</button>
    
          <div class="blur">
            <input v-model="blur" type="range" id="range" name="range" step="1" min="0" max="100"/>
            <button>brur: {{ blur }}</button>
          </div>
    
          <div class="says">
            <input type="text" id="catSay"/>
            <label for="catSay">Кот говорит!</label>
          </div>
        </div>
      </footer>
</template>