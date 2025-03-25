<script setup>
  import { reactive, ref } from 'vue'

  const btnClass = reactive({
    water: 'hydro',
    fire: 'pyro',
    wind: 'anemo'
  })
  const count = ref(0)
  function increment() {
    count.value++
  }
</script>

<template>
  <!-- @click is shorthand for v-on:click -->
  <button :class="btnClass.water" v-on:click="increment">Count is: {{ count }}</button><br>
  <button :class="btnClass.fire" @click="increment">Count is: {{ count }}</button><br>
  <button :class="btnClass.wind" @click="increment">Count is: {{ count }}</button>
</template>

<style>
  button {
    padding: 0.5em;
    margin: 1.5em;
  }
  .hydro {
    color: blue;
  }
  .pyro {
    color: orange;
  }
  .anemo {
    color: turquoise;
    background-color: #333333;
  }
</style>
