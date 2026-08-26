<script setup lang="ts">

import { NCard } from 'naive-ui';
import { CardThemeVars } from 'naive-ui/es/card/styles';

const cardOverrides : Partial<CardThemeVars> = {
  borderColor: '#1D5DEC',
  borderRadius: '8px',
  titleFontSizeSmall: '20pt',
  fontSizeSmall: '16pt'
}

</script>

<template>
  <n-card
    hoverable
    size="small"
    :theme-overrides="cardOverrides"
  >
    <template #header>
      RPCS4 is your PlayStation™ 4 emulator.
    </template>
    <div class="body-text">
      Use only with lawfully obtained archival copies of PS4 games you physically own. <strong>RPCS4 is non-commercial and is not affiliated with Sony or PlayStation.</strong>
    </div>
  </n-card>
</template>

<style scoped>
  .n-card {
    max-width: 600px;
    line-height: 2.8em;
  }
</style>