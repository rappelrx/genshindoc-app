<script setup>
  import { ref, onMounted } from 'vue'

  const checkedNames = ref([])
  const name = ref('')

  // No longer need to use event handler when using v-model
  /*function onInput(e) {
    name.value = e.target.value
  }*/

  // For manual DOM manipulation...
  const kiraraRef = ref(null)
  const disclaimerRef = ref(null)
  onMounted(() => {
    // Component now mounted. Able to access template refs at this time of component's lifecycle.
    if (kiraraRef.value.value === 'Kirara from Inazuma')
    	disclaimerRef.value.textContent = 'Disclaimer: Including birthplace is optional.'
  })
</script>

<template>
  <div class="row">
    <div class="col">
      <p>Checked names: {{ checkedNames }}</p>
      <input type="checkbox" id="yanfei" value="Yanfei from Liyue" v-model="checkedNames">
      <label for="yanfei">Yanfei</label>
      <input type="checkbox" id="bennett" value="Bennett from Mondstadt" v-model="checkedNames">
      <label for="bennett">Bennett</label>
      <input ref="kiraraRef" type="checkbox" id="kirara" value="Kirara from Inazuma" v-model="checkedNames">
      <label for="kirara">Kirara</label>
    </div>
    <div class="col">
      <!-- <input :value="text" @input="onInput" placeholder="Type your name here"> -->
      <input v-model="name" placeholder="Type your name here">
      <p>My name is: {{ name }}</p>
      <textarea v-model="name" placeholder="Add multiple lines"></textarea>
      <p>Name as a multiline message:</p>
      <p style="white-space: pre-line;">{{ name }}</p>
      <p ref="disclaimerRef" style="font-style: italic; font-size: small;"></p>
    </div>
  </div>
</template>

<style>
  .row {
    display: table;
    width: 100%;
  }
  .col {
    display: table-cell;
  }
</style>
