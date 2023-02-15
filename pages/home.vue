<script setup lang="ts">
import { ChildProcess } from 'child_process'
import { useI18n } from 'vue-i18n'

definePageMeta({
  middleware: 'auth',
  alias: ['/signin/callback'],
})

const route = useRoute()
const router = useRouter()
if (process.client && route.path === '/signin/callback')
  router.push('/home')

const { t } = useI18n()
useHeadFixed({
  title: () => t('nav.home'),
})

const reRenderKey = ref(0)
const reRender = () => reRenderKey.value += 1
</script>

<template>
  <MainContent>
    <template #title>
      <NuxtLink to="/home" timeline-title-style flex items-center gap-2 @click="reRender">
        <div i-ri:home-5-line />
        <span>{{ $t('nav.home') }}</span>
      </NuxtLink>
    </template>

    <TimelineHome v-if="isHydrated" :key="reRenderKey" />
  </MainContent>
</template>
