<script setup lang="ts">
	import QuestsList from './components/QuestsToDoWithFilter.vue'
  import CharacterSearch from './components/WatchGenshinChar.vue'
  import WishConverter from './components/WishConverter.vue'
</script>

<template>
  <img src="./assets/figma/baron-bunny-papercraft.png" class="logo" alt="Baron bunny" />
  <img src="./assets/figma/aranara-with-lyre.png" class="logo" alt="Aranara with lyre" />
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

<style scoped>
  .logo {
    height: 10em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
</style>
