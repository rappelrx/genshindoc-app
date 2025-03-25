<script setup>
  import { ref } from 'vue'
  
  const visionClass = ref('vision')
</script>


<template>
  <h1 v-bind:class="visionClass">Pyro represents fire</h1>
</template>


<style>
  .vision {
    color: red;
    animation: rotation 1.5s infinite linear;
  }
  @keyframes rotation {
    0% {
      transform: rotate(0deg);
    }
    50% {
      transform: rotate(-12deg);
    }
    100% {
      transform: rotate(0deg);
    }
  }
</style>
