<script setup lang="ts">
definePageMeta({
  middleware: 'auth',
})

const { t } = useI18n()

useHeadFixed({
  title: () => t('nav.favourites'),
})

const reRenderKey = ref(0)
const reRender = () => reRenderKey.value += 1
</script>

<template>
  <MainContent>
    <template #title>
      <NuxtLink to="/favourites" timeline-title-style flex items-center gap-2 @click="reRender">
        <div i-ri:heart-3-line />
        <span>{{ t('nav.favourites') }}</span>
      </NuxtLink>
    </template>

    <TimelineFavourites v-if="isHydrated" :key="reRenderKey" />
  </MainContent>
</template>
