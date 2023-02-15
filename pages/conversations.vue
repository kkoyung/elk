<script setup lang="ts">
definePageMeta({
  middleware: 'auth',
})

const { t } = useI18n()

useHeadFixed({
  title: () => t('nav.conversations'),
})

const reRenderKey = ref(0)
const reRender = () => reRenderKey.value += 1
</script>

<template>
  <MainContent>
    <template #title>
      <NuxtLink to="/conversations" timeline-title-style flex items-center gap-2 @click="reRender">
        <div i-ri:at-line />
        <span>{{ t('nav.conversations') }}</span>
      </NuxtLink>
    </template>

    <TimelineConversations v-if="isHydrated" :key="reRenderKey" />
  </MainContent>
</template>
