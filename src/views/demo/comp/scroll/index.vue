<template>
  <PageWrapper content="基于el-scrollbar" title="滚动组件示例">
    <div class="scroll-wrap">
      <ScrollContainer class="mt-4">
        <ul class="p-3">
          <template v-for="index in 100" :key="index">
            <li :style="{ border: '1px solid #eee' }" class="p-2">
              {{ index }}
            </li>
          </template>
        </ul>
      </ScrollContainer>
    </div>
  </PageWrapper>
</template>
<script lang="ts">
  import { defineComponent } from 'vue';
  import { ScrollContainer } from '/@/components/Container/index';
  import { PageWrapper } from '/@/components/Page';

  export default defineComponent({
    components: { ScrollContainer, PageWrapper },
  });
</script>
<style lang="less" scoped>
  .scroll-wrap {
    width: 50%;
    height: 300px;
    background-color: @component-background;
  }
</style>
