<script setup>
	import QuestsList from './QuestsToDoWithFilter.vue'
  import CharacterSearch from './WatchGenshinChar.vue'
  import WishConverter from './WishConverter.vue'
</script>

<template>
  <QuestsList head="Quests">
    <template #subtitle>
      Keep track of your quests with this to-do list.
    </template>
  </QuestsList>
  <CharacterSearch head="Character Search">
    <template #subtitle>
    	Fetch description of character from genshin.dev API.
    </template>
  </CharacterSearch>
  <WishConverter head="Wish Converter">
    <template #subtitle>
      Convert from primogems to wishes or vice versa.
    </template>
  </WishConverter>
</template>

<style>
  html {
    padding: 0 30px 20px;
  }
  h2 {
    margin-top: 35px;
  }
  form {
    margin-top: 10px;
  }
  button {
    margin-left: 4px;
    transition: box-shadow 0.5s;
  }
  button:hover {
    box-shadow: 0 4px 8px rgba(0,0,0,0.50);
  }
</style>