<script setup lang="ts">

const { t } = useI18n()

useHeadFixed({
  title: () => t('title.local_timeline'),
})

const reRenderKey = ref(0)
const reRender = () => reRenderKey.value += 1
</script>

<template>
  <MainContent>
    <template #title>
      <NuxtLink to="/public/local" timeline-title-style flex items-center gap-2 @click="reRender">
        <div i-ri:group-2-line />
        <span>{{ t('title.local_timeline') }}</span>
      </NuxtLink>
    </template>

    <TimelinePublicLocal v-if="isHydrated" :key="reRenderKey" />
  </MainContent>
</template>
