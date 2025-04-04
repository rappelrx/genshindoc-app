<script setup lang="ts">
    import { ref, watchEffect } from 'vue'

    const props = defineProps<{
        head?: String
    }>()

    const PRIMO_PER_WISH: number = 160
    const primogem = ref<number>(PRIMO_PER_WISH)
    const wish = ref<number>(1)
    const primoRemainder = ref<number>(0)

    const setPrimos = (e: Event, v: number = +(<HTMLInputElement>e.target).value): void => {
        const validV: number = v < 0 ? 0 : Math.floor(v)
        primogem.value = validV
        wish.value = Math.floor(validV / PRIMO_PER_WISH)
    }

    const setWishes = (e: Event, v: number = +(<HTMLInputElement>e.target).value): void => {
        const validV: number = v < 0 ? 0 : Math.floor(v)
        wish.value = validV
        primogem.value = (validV * PRIMO_PER_WISH)
    }

    watchEffect(() => {
        primoRemainder.value = primogem.value - (wish.value * PRIMO_PER_WISH)
    })
</script>

<template>
  <h2>{{ head || 'No props passed yet' }}</h2>
  <slot name="subtitle">***Fallback message; add text in parent component.***</slot>
  <form @submit.prevent="addQuest">
    <input type="number" min="0" :value="primogem" @change="setPrimos"> primogems =
    <input type="number" min="0" :value="wish" @change="setWishes"> wishes
  </form>
  <p>With {{ primogem }} primogems, you can make {{ wish }} wishes, leaving you with {{ primoRemainder }} primogems left over.</p>
</template>