<script setup lang="ts">
  import { ref, watch } from 'vue'
  
  const props = defineProps<{
    head?: String
  }>()

  const character = ref<string>('')
  const submitted = ref<boolean>(false)
  const result = ref<string>('Character description will be displayed here.')

  // watch works directly on a ref
  // pseudo for watch(): if submitted's value changes, then execute the async function
  watch(submitted, async () => {
    result.value = "Searching for character..."
    character.value = character.value.replace(/\s+/g, '-')	// replace spaces with dashes
    try {
      // using genshin.dev API
      const res: Response = await fetch(`https://genshin.jmp.blue/characters/${character.value}`)
      /* result.value = (await res.json()).description */
      const data: { description: string; error?: string } = await res.json()
      result.value = data.description
      /* if (result.value.error != null) throw 'invalid name' */
      if (data.error != null) throw 'invalid name'
    } catch (error: unknown) {
      result.value = 'Oops! No records found for ' + character.value + '. Error: ' + error
    } finally {
      submitted.value = false
    }
  })
</script>

<template>
  <h2>{{ head || 'No props passed yet' }}</h2>
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