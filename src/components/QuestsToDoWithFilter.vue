<script setup lang="ts">
  import { ref, computed } from 'vue'
  import type { Ref } from 'vue'

  defineProps<{
    head?: String
  }>()
  
  let id: number = 0	// give each quest a unique id
  const newQuest: Ref<string> = ref('')
  const hideCompleted: Ref<boolean> = ref(false)
  const quests: Ref<Array<{ id: number; text: string; done: boolean }>> = ref([
    { id: id++, text: 'Give five sunsettias to Bennett', done: true },
    { id: id++, text: 'Defeat the hilichurls in Wolvendom', done: true },
    { id: id++, text: 'Cook three servings of goulash', done: false }
  ])
  
  /* hideCompleted true ? 
  		yes, return filtered list : 
      no, return full list */
  const filteredQuests = computed(() => {
    return hideCompleted.value ?
      quests.value.filter((item) => !item.done) :
    	quests.value
  })

  function addQuest(): void {
    quests.value.push({ id: id++, text: newQuest.value, done: false })
    newQuest.value = ''
  }

  function removeQuest(quest: { id: number; text: string; done: boolean }): void {
    quests.value = quests.value.filter((item) => item !== quest)
  }
</script>

<template>
  <h2>{{ head || 'No props passed yet' }}</h2>
  <slot name="subtitle">***Fallback message; add text in parent component.***</slot>
  <form @submit.prevent="addQuest">
    <input v-model="newQuest" required placeholder="type new quest">
    <button>Add Quest</button>
  </form>
  <ul>
    <li v-for="quest in filteredQuests" :key="quest.id">
      <input type="checkbox" v-model="quest.done">
      <span :class="{ done: quest.done }">{{ quest.text }}</span>
      <button @click="removeQuest(quest)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>
</template>

<style>
  li {
    padding-bottom: 4px;
  }
  li > button {
    color: red;
    font-weight: bolder;
  }
  .done {
    text-decoration: line-through;
  }
</style>