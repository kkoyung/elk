<script setup lang="ts">


const { t } = useI18n()

useHeadFixed({
  title: () => t('title.federated_timeline'),
})

const reRenderKey = ref(0)
const reRender = () => reRenderKey.value += 1
</script>

<template>
  <MainContent>
    <template #title>
      <NuxtLink to="/public" timeline-title-style flex items-center gap-2 @click="reRender">
        <div i-ri:earth-line />
        <span>{{ t('title.federated_timeline') }}</span>
      </NuxtLink>
    </template>

    <TimelinePublic v-if="isHydrated" :key="reRender" />
  </MainContent>
</template>
