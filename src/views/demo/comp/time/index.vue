<template>
  <PageWrapper title="时间组件示例">
    <CollapseContainer title="基础示例">
      <Time :value="time1" />
      <br />
      <Time :value="time2" />
    </CollapseContainer>

    <CollapseContainer class="my-4" title="定时更新">
      <Time :step="1" :value="now" />
      <br />
      <Time :step="5" :value="now" />
    </CollapseContainer>

    <CollapseContainer title="定时更新">
      <Time :value="now" mode="date" />
      <br />
      <Time :value="now" mode="datetime" />
      <br />
      <Time :value="now" />
    </CollapseContainer>
  </PageWrapper>
</template>
<script lang="ts">
  import { defineComponent, reactive, toRefs } from 'vue';
  import { PageWrapper } from '/@/components/Page';
  import { Time } from '/@/components/Time';
  import { CollapseContainer } from '/@/components/Container/index';

  export default defineComponent({
    components: { PageWrapper, Time, CollapseContainer },
    setup() {
      const now = new Date().getTime();
      const state = reactive({
        time1: now - 60 * 3 * 1000,
        time2: now - 86400 * 3 * 1000,
      });
      return {
        ...toRefs(state),
        now,
      };
    },
  });
</script>
