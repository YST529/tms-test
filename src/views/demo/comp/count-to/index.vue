<template>
  <PageWrapper title="数字动画示例">
    <Card>
      <CardGrid class="count-to-demo-card">
        <CountTo :color="'#409EFF'" :duration="8000" :endVal="200000" :startVal="1" prefix="$" />
      </CardGrid>
      <CardGrid class="count-to-demo-card">
        <CountTo
          :color="'red'"
          :decimals="2"
          :duration="6000"
          :endVal="300000"
          :startVal="1"
          suffix="$"
        />
      </CardGrid>
      <CardGrid class="count-to-demo-card">
        <CountTo
          :color="'rgb(0,238,0)'"
          :duration="7000"
          :endVal="400000"
          :startVal="1"
          suffix="$"
        />
      </CardGrid>
      <CardGrid class="count-to-demo-card">
        <CountTo
          :color="'rgba(138,43,226,.6)'"
          :duration="8000"
          :endVal="500000"
          :startVal="10000"
          separator="-"
        />
      </CardGrid>
    </Card>
  </PageWrapper>
</template>
<script lang="ts">
  import { defineComponent } from 'vue';
  import { Card } from 'ant-design-vue';
  import { CountTo } from '/@/components/CountTo/index';
  import { PageWrapper } from '/@/components/Page';

  export default defineComponent({
    components: {
      Card,
      CardGrid: Card.Grid,
      CountTo,
      PageWrapper,
    },
  });
</script>
<style lang="less" scoped>
  .count-to-demo {
    &-card {
      width: 50%;
      font-size: 30px;
      text-align: center;
    }
  }
</style>
