<template>
  <vue-json-pretty :data="data" :deep="3" :path="'res'" :showLength="true" />
</template>

<script lang="ts" setup>
  import VueJsonPretty from 'vue-json-pretty';
  import 'vue-json-pretty/lib/styles.css';

  defineProps({
    data: Object,
  });
</script>
