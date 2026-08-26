<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { NText, NGradientText } from 'naive-ui';

function getTime() {
  const developmentStart = new Date(2023, 5, 1); // June 2023
  const today = new Date();

  const months =
    (today.getFullYear() - developmentStart.getFullYear()) * 12 +
    today.getMonth() - developmentStart.getMonth();

  const time_result = [
    Math.floor(months / 12),
    months % 12
  ];

  return months >= 12
    ? `${time_result[0]} years${time_result[1] > 0 ? `, ${time_result[1]} months` : ''}`
    : `${months} months`;
}

const contributors = ref<string | number>('1+');

onMounted(async () => {
  try {
    const response = await fetch(
      'https://api.github.com/repos/RPCS4/RPCS4.github.io/contributors?per_page=100'
    );
    if (response.ok) {
      const data = await response.json();
      if (Array.isArray(data)) {
        contributors.value = data.length;
      }
    }
  } catch (e) {
    console.error('Failed to fetch contributors:', e);
  }
});
</script>

<template>
  <div class="hook">
    <div class="hook-item">
      <n-gradient-text
        id="emu-name"
        type="info"
      >
        RPCS4
      </n-gradient-text>

      <n-gradient-text type="info">
        {{ getTime() }}
      </n-gradient-text>

      <n-text>of development.</n-text>
    </div>

    <div class="hook-item">
      <n-gradient-text type="info">
        {{ contributors }}
      </n-gradient-text>

      <n-text>experienced contributors.</n-text>
    </div>
  </div>
</template>

<style scoped>
.hook {
  display: flex;
  flex-flow: column nowrap;
  gap: 20px;
}

.hook-item {
  padding: 4px 0px;
  display: flex;
  flex-flow: column nowrap;
}

.n-gradient-text {
  font-size: 2.5em;
}

.n-text {
  font-size: 1.5em;
  font-weight: bold;
}

#emu-name {
  font-family: 'Rave';
  font-size: calc(5vw + 5vh);
}

@font-face {
  font-family: "Rave";
  src: url('/fonts/Font.otf');
}
</style>
