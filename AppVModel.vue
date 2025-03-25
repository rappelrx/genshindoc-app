<script setup>
	import QuestsList from './QuestsToDoWithFilter.vue'
  import CharacterSearch from './WatchGenshinChar.vue'
</script>

<template>
  <h2>Quests</h2>
  <QuestsList />
  <h2>Character Search</h2>
  <CharacterSearch />
</template>

<style>
  html {
    padding: 0 30px 20px;
  }
  h2 {
    margin-top: 30px;
  }
</style>
