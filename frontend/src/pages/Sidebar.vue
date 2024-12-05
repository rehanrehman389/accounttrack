<template>
  <div
    class="flex flex-col border-r border-gray-200 bg-gray-50 h-screen duration-300 ease-in-out"
    :class="{
      'w-64': isExpanded,
      'w-16': !isExpanded,
    }"
  >
    <div
      v-for="(item, index) in menuItems"
      :key="index"
      class="flex items-center gap-2 p-2 cursor-pointer hover:bg-gray-100 rounded"
      :class="{'justify-center': !isExpanded}"
    >
      <!-- Smaller Icon -->
      <Icon :icon="item.icon" class="h-4 w-4 text-gray-700" />
      <span v-if="isExpanded">{{ item.label }}</span>
    </div>
    <div class="grow"></div>
    <div
      class="flex items-center gap-2 p-2 cursor-pointer hover:bg-gray-100 rounded"
      @click="toggleSidebar"
      :class="{'justify-center': !isExpanded}"
    >
      <Icon
        :icon="isExpanded ? 'mdi:arrow-collapse-left' : 'mdi:arrow-expand-right'"
        class="h-4 w-4 text-gray-700"
      />
      <span v-if="isExpanded">Collapse</span>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Icon } from '@iconify/vue';

const isExpanded = ref(true);

const menuItems = [
  { label: 'Search', icon: 'mdi:magnify' },
  { label: 'Notifications', icon: 'mdi:bell' },
  { label: 'Dashboard', icon: 'mdi:view-dashboard-outline' },
  { label: 'Settings', icon: 'mdi:cog-outline' },
];

function toggleSidebar() {
  isExpanded.value = !isExpanded.value;
}
</script>
