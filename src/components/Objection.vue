<script setup>
  import { ref } from 'vue'
  
  const objection = ref(true)
  
  function toggle() {
    objection.value = !objection.value
  }
</script>

<template>
  <button @click="toggle">Top-page Toggle</button>
  <h1 v-if="objection" id="objection">Objection!</h1>
  <h1 v-else>Cannot object...</h1>
  
  <h2 v-if="objection">Inadmissible evidence!</h2>
  <h2 v-else>Oh no 😢</h2>
  <button @click="objection = !objection">Bottom-page Toggle</button>
</template>

<style>
  @keyframes chaos {
    0% {
      transform: translate(0,0) scale(1);
    }
    25% {
      transform: translate(-10px,-10px) scale(0.9);
    }
    50% {
      transform: translate(75px,0) scale(1.1);
    }
    75% {
      transform: translate(-10px,10px) scale(0.9);
    }
    100% {
      transform: translate(0,0) scale(1);
    }
  }
  #objection {
    color: red;
    animation: chaos 2s infinite linear;
  }
  button:hover {
    box-shadow: 0 4px 8px black;
  }
  button:active {
    box-shadow: 0 2px 4px red;
  }
</style>
