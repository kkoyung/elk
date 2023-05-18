<script setup lang="ts">
definePageMeta({
  middleware: 'auth',
})

const { t } = useI18n()

useHydratedHead({
  title: () => t('nav.bookmarks'),
})

const reRenderKey = ref(0)
const reRender = () => reRenderKey.value += 1
</script>

<template>
  <MainContent>
    <template #title>
      <NuxtLink to="/bookmarks" timeline-title-style flex items-center gap-2 @click="reRender">
        <div i-ri:bookmark-line />
        <span>{{ t('nav.bookmarks') }}</span>
      </NuxtLink>
    </template>

    <TimelineBookmarks v-if="isHydrated" :key="reRenderKey" />
  </MainContent>
</template>
