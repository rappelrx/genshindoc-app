<script setup>
  import { ref } from 'vue'

  // give each quest a unique id
  let id = 0

  const newQuest = ref('')
  const quests = ref([
    { id: id++, text: 'Give five sunsettias to Bennett' },
    { id: id++, text: 'Defeat the hilichurls in Wolvendom' },
    { id: id++, text: 'Cook three servings of goulash' }
  ])

  /* Push new item into the 'quests' array */
  function addQuest() {
    quests.value.push({ id: id++, text: newQuest.value })
    newQuest.value = ''	  // value is taken care of by v-model="newQuest"
  }

  /* Replace the 'quests' array with a new one */
  function removeQuest(quest) {
    quests.value = quests.value.filter((item) => item != quest )
  }
</script>

<template>
  <form @submit.prevent="addQuest">
    <input v-model="newQuest" required placeholder="type new quest">
    <button>Add Quest</button>
  </form>
  <ul>
    <li v-for="quest in quests" :key="quest.id">
      {{ quest.text }}
      <button @click="removeQuest(quest)">X</button>
    </li>
  </ul>
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
</style>
