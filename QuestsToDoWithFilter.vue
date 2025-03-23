<script setup>
  import { ref, computed } from 'vue'

  let id = 0	// give each quest a unique id

  const newQuest = ref('')
  const hideCompleted = ref(false)
  const quests = ref([
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

  function addQuest() {
    quests.value.push({ id: id++, text: newQuest.value, done: false })
    newQuest.value = ''
  }

  function removeQuest(quest) {
    quests.value = quests.value.filter((item) => item !== quest)
  }
</script>

<template>
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
  button {
    margin-left: 4px;
    transition: box-shadow 0.5s;
  }
  button:hover {
    box-shadow: 0 4px 8px rgba(0,0,0,0.50);
  }
  .done {
    text-decoration: line-through;
  }
</style>
