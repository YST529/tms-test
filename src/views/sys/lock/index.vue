<template>
  <transition mode="out-in" name="fade-bottom">
    <LockPage v-if="getIsLock" />
  </transition>
</template>
<script lang="ts" setup>
  import { computed } from 'vue';
  import LockPage from './LockPage.vue';
  import { useLockStore } from '/@/store/modules/lock';

  const lockStore = useLockStore();
  const getIsLock = computed(() => lockStore?.getLockInfo?.isLock ?? false);
</script>
