<script setup>
	import QuestsList from './QuestsToDoWithFilter.vue'
  import CharacterSearch from './WatchGenshinChar.vue'
</script>

<template>
  <QuestsList head="Quests" />
  <CharacterSearch head="Character Search" />
</template>

<style>
  html {
    padding: 0 30px 20px;
  }
  h2 {
    margin-top: 30px;
  }
</style>