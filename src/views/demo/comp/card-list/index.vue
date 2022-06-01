<template>
  <PageWrapper content="基础封装" title="卡片列表示例">
    <CardList :api="demoListApi" :params="params" @delete="handleDel" @get-method="getMethod">
      <template #header>
        <Button color="error" type="primary"> 按钮1 </Button>
        <Button color="success" type="primary"> 按钮2 </Button>
      </template>
    </CardList>
  </PageWrapper>
</template>
<script lang="ts" setup>
  import { CardList } from '/@/components/CardList';
  import { Button } from '/@/components/Button';
  import { PageWrapper } from '/@/components/Page';
  import { demoListApi } from '/@/api/demo/table';
  import { useMessage } from '/@/hooks/web/useMessage';
  const { notification } = useMessage();
  // 请求api时附带参数
  const params = {};

  let reload = () => {};
  // 获取内部fetch方法;
  function getMethod(m: any) {
    reload = m;
  }
  //删除按钮事件
  function handleDel(id) {
    console.log(id);
    notification.success({ message: `成功删除${id}` });
    reload();
  }
</script>
