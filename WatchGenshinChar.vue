<script setup>
  import { ref, watch } from 'vue'

  const character = ref('')
  const submitted = ref(false)
  const result = ref('Character description will be displayed here.')

  // watch works directly on a ref
  // pseudo for watch(): if submitted's value changes, then execute the async function
  watch(submitted, async () => {
    result.value = "Searching for character..."
    character.value = character.value.replace(/\s+/g, '-')	// replace spaces with dashes
    try {
      // using genshin.dev API
      const res = await fetch(`https://genshin.jmp.blue/characters/${character.value}`)
      result.value = (await res.json()).description
      if (result.value.error != null) throw 'invalid character'
    } catch (error) {
      result.value = 'Error! No records found for ' + character.value + '. ' + error
    } finally {
      submitted.value = false
    }
  })
</script>

<template>
  <p><strong>Get description of character from Genshin Impact.</strong></p>
  <p>
    <input v-model="character" placeholder="Input character..." />
    <button @click="submitted = true">Search</button>
  </p>
  <p>{{ result }}</p>
</template>

<style>
  button {
    margin-left: 4px;
    transition: box-shadow 0.5s;
  }
  button:hover {
    box-shadow: 0 4px 8px rgba(0,0,0,0.5);
  }
</style>
