<script lang="ts" setup>
import type { FUniver, Univer } from '@univerjs/presets'
import { UniverSheetsCorePreset } from '@univerjs/preset-sheets-core'
import UniverPresetSheetsCoreEnUS from '@univerjs/preset-sheets-core/locales/en-US'
import { createUniver, LocaleType, mergeLocales } from '@univerjs/presets'
import { onBeforeUnmount, onMounted, ref } from 'vue'

import '@univerjs/preset-sheets-core/lib/index.css'

const container = ref<HTMLElement | null>(null)

let univerInstance: Univer | null = null
let univerAPIInstance: FUniver | null = null

onMounted(() => {
  const { univer, univerAPI } = createUniver({
    locale: LocaleType.EN_US,
    locales: {
      [LocaleType.EN_US]: mergeLocales(UniverPresetSheetsCoreEnUS),
    },
    presets: [
      UniverSheetsCorePreset({
        container: container.value as HTMLElement,
      }),
    ],
  })

  univerAPI.createWorkbook({})

  univerInstance = univer
  univerAPIInstance = univerAPI
})

onBeforeUnmount(() => {
  univerInstance?.dispose()
  univerAPIInstance?.dispose()
  univerInstance = null
  univerAPIInstance = null
})
</script>

<template>
  <div ref="container" />
</template>
