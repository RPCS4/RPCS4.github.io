<script setup lang="ts">
import { h, ref, Component } from 'vue'
import { NIcon, MenuOption } from 'naive-ui'
import {
  Code as CodeIcon,
  Book as BookIcon,
  LogoDiscord as DiscordIcon
} from '@vicons/carbon'

function renderIcon(icon: Component) {
  return () => h(NIcon, null, { default: () => h(icon) })
}

const activeKey = ref<string | null>(null)

const menuOptions: MenuOption[] = [
  {
    label: () =>
      h(
        'a',
        {
          href: 'https://github.com/RPCS4/RPCS4.github.io',
          target: '_blank',
          rel: 'noopener noreferrer'
        },
        'development'
      ),
    key: 'development',
    icon: renderIcon(CodeIcon)
  },
  {
    label: () =>
      h(
        'a',
        {
          href: 'https://github.com/RPCS4/RPCS4.github.io/wiki',
          target: '_blank',
          rel: 'noopener noreferrer'
        },
        'wiki'
      ),
    key: 'wiki',
    icon: renderIcon(BookIcon)
  },
  {
    label: () =>
      h(
        'a',
        {
          href: 'https://discord.com/invite/gqz8APTfbE',
          target: '_blank',
          rel: 'noopener noreferrer'
        },
        'discuss'
      ),
    key: 'discuss',
    icon: renderIcon(DiscordIcon)
  }
]
</script>

<template>
  <div class="bar-wrapper">
    <n-button
      quaternary
      tag="a"
      href="/"
    >
      <img
        alt="RPCS4 logo"
        class="logo"
        src="/assets/logo-dark.png"
        width="32"
        height="32"
      >
    </n-button>
    <n-menu
      v-model:value="activeKey"
      mode="horizontal"
      :options="menuOptions"
    />
  </div>
</template>

<style scoped>
.bar-wrapper {
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  justify-content: space-between;
  margin: 8px;
}
</style>
