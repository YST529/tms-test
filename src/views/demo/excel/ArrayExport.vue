<template>
  <PageWrapper content="根据数组格式的数据进行导出" title="导出示例">
    <BasicTable :columns="columns" :dataSource="data" title="基础表格">
      <template #toolbar>
        <a-button @click="aoaToExcel"> 导出 </a-button>
      </template>
    </BasicTable>
  </PageWrapper>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import { BasicTable } from '/@/components/Table';
  import { aoaToSheetXlsx } from '/@/components/Excel';
  import { arrHeader, arrData, columns, data } from './data';
  import { PageWrapper } from '/@/components/Page';

  export default defineComponent({
    components: { BasicTable, PageWrapper },
    setup() {
      function aoaToExcel() {
        // 保证data顺序与header一致
        aoaToSheetXlsx({
          data: arrData,
          header: arrHeader,
          filename: '二维数组方式导出excel.xlsx',
        });
      }

      return {
        aoaToExcel,
        columns,
        data,
      };
    },
  });
</script>
