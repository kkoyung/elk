<script setup lang="ts">
definePageMeta({
  middleware: 'auth',
})

const { t } = useI18n()

useHeadFixed({
  title: () => t('account.pinned'),
})

const reRenderKey = ref(0)
const reRender = () => reRenderKey.value += 1
</script>

<template>
  <MainContent>
    <template #title>
      <NuxtLink to="/public/pinned" timeline-title-style flex items-center gap-2 @click="reRender">
        <div i-ri:pushpin-line />
        <span>{{ t('account.pinned') }}</span>
      </NuxtLink>
    </template>

    <TimelinePinned v-if="isHydrated && currentUser" :key="reRenderKey" />
  </MainContent>
</template>
