<template>
  <PageWrapper
    content=" 基础组件依赖于ant-design-vue,组件库已有的基础组件,项目中不会再次进行demo展示（二次封装组件除外）"
    contentFullHeight
    title="基础组件"
  >
    <a-row :gutter="[20, 20]">
      <a-col :lg="24" :xl="10">
        <a-card title="BasicButton Color">
          <div class="my-2">
            <h3>success</h3>
            <div class="py-2">
              <a-button color="success"> 成功 </a-button>
              <a-button class="ml-2" color="success" disabled> 禁用 </a-button>
              <a-button class="ml-2" color="success" loading> loading </a-button>
              <a-button class="ml-2" color="success" type="link"> link </a-button>
              <a-button class="ml-2" color="success" loading type="link"> loading link </a-button>
              <a-button class="ml-2" color="success" disabled type="link"> disabled link </a-button>
            </div>
          </div>

          <div class="my-2">
            <h3>warning</h3>
            <a-button color="warning"> 警告 </a-button>
            <a-button class="ml-2" color="warning" disabled> 禁用 </a-button>
            <a-button class="ml-2" color="warning" loading> loading </a-button>
            <a-button class="ml-2" color="warning" type="link"> link </a-button>
            <a-button class="ml-2" color="warning" loading type="link"> loading link </a-button>
            <a-button class="ml-2" color="warning" disabled type="link"> disabled link </a-button>
          </div>

          <div class="my-2">
            <h3>error</h3>
            <a-button color="error"> 错误 </a-button>
            <a-button class="ml-2" color="error" disabled> 禁用 </a-button>
            <a-button class="ml-2" color="error" loading> loading </a-button>
            <a-button class="ml-2" color="error" type="link"> link </a-button>
            <a-button class="ml-2" color="error" loading type="link"> loading link </a-button>
            <a-button class="ml-2" color="error" disabled type="link"> disabled link </a-button>
          </div>

          <div class="my-2">
            <h3>ghost</h3>
            <a-button class="ml-2" color="success" ghost> 幽灵成功 </a-button>
            <a-button class="ml-2" color="warning" ghost> 幽灵警告 </a-button>
            <a-button class="ml-2" color="error" ghost> 幽灵错误 </a-button>
            <a-button class="ml-2" color="warning" ghost type="dashed"> 幽灵警告dashed </a-button>
            <a-button class="ml-2" danger ghost> 幽灵危险 </a-button>
          </div>
        </a-card>
      </a-col>
      <a-col :lg="24" :xl="14">
        <a-card title="BasicButton Types">
          <div class="my-2">
            <h3>primary</h3>
            <a-button preIcon="mdi:page-next-outline" type="primary"> 主按钮 </a-button>
            <a-button class="ml-2" disabled type="primary"> 禁用 </a-button>
            <a-button class="ml-2" danger preIcon="mdi:page-next-outline" type="primary">
              危险
            </a-button>
            <a-button class="ml-2" loading type="primary"> loading </a-button>
            <a-button class="ml-2" type="link"> link </a-button>
            <a-button class="ml-2" loading type="link"> loading link </a-button>
            <a-button class="ml-2" disabled type="link"> disabled link </a-button>
          </div>

          <div class="my-2">
            <h3>default</h3>
            <a-button type="default"> 默认 </a-button>
            <a-button class="ml-2" disabled type="default"> 禁用 </a-button>
            <a-button class="ml-2" danger type="default"> 危险 </a-button>
            <a-button class="ml-2" loading type="default"> loading </a-button>
            <a-button class="ml-2" type="link"> link </a-button>
            <a-button class="ml-2" loading type="link"> loading link </a-button>
            <a-button class="ml-2" disabled type="link"> disabled link </a-button>
          </div>

          <div class="my-2">
            <h3>dashed</h3>
            <a-button type="dashed"> dashed </a-button>
            <a-button class="ml-2" disabled type="dashed"> 禁用 </a-button>
            <a-button class="ml-2" danger type="dashed"> 危险 </a-button>
            <a-button class="ml-2" loading type="dashed"> loading </a-button>
          </div>

          <div class="my-2">
            <h3>ghost 常规幽灵按钮通常用于有色背景下</h3>
            <div class="bg-gray-400 py-2">
              <a-button class="ml-2" ghost type="primary"> 幽灵主要 </a-button>
              <a-button class="ml-2" ghost type="default"> 幽灵默认 </a-button>
              <a-button class="ml-2" ghost type="dashed"> 幽灵dashed </a-button>
              <a-button class="ml-2" disabled ghost type="primary"> 禁用 </a-button>
              <a-button class="ml-2" ghost loading type="primary"> loading </a-button>
            </div>
            <!-- antd 按钮不能同时使用ghost和link -->
            <!--      <a-button ghost type="link" class="ml-2"> link </a-button>-->
            <!--      <a-button ghost type="link" class="ml-2" loading> loading link </a-button>-->
            <!--      <a-button ghost type="link" class="ml-2" disabled> disabled link </a-button>-->
          </div>
        </a-card>
      </a-col>
    </a-row>
  </PageWrapper>
</template>
<script lang="ts">
  import { defineComponent } from 'vue';
  import { PageWrapper } from '/@/components/Page';
  import { Card, Row, Col } from 'ant-design-vue';
  export default defineComponent({
    components: { PageWrapper, ACard: Card, ARow: Row, ACol: Col },
  });
</script>
