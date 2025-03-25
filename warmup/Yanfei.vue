<script setup>
	import { reactive, ref } from 'vue'

  const yanfei = reactive({
    age: 17,
    vision: 'none',
    residence: 'Fontaine',
    job: 'legal intern'
  })
  const dialogue = ref('Not ready for trial.')
  
  // After one year...
  yanfei.age++
  yanfei.vision = 'pyro'
  yanfei.residence = 'Liyue'
  yanfei.job = 'lawyer'
  dialogue.value = 'Ready for trial!'
</script>


<template>
  <h1>Yanfei says: {{dialogue}}</h1>
  <p>
    Yanfei is an {{yanfei.age}} year old {{yanfei.job}} living in {{yanfei.residence}}.
  </p>
</template>
