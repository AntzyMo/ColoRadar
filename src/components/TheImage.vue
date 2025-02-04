<script setup lang="ts">
  import ColorThief from 'colorthief'

  const { imgs } = defineProps<{
    imgs: string[]
  }>()

  const imgsRef = useTemplateRef('img')
  const colorThief = new ColorThief()

  function handleImg(index: number) {
    const img = imgsRef.value?.[index]
    const color = colorThief.getColor(img)
    console.log(color)
  }
</script>

<template>
  <div
    class="w-682px"
    bg-blue
  >
    <img
      v-for="(item, index) in imgs"
      ref="img"
      :key="item"
      :src="item"
      class="w-full block rounded-2xl"
      @click="handleImg(index)"
    >
  </div>
</template>
