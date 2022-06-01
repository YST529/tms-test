<template>
  <PageWrapper title="水印示例">
    <CollapseContainer class="w-full h-32 bg-white rounded-md" title="Global WaterMark">
      <a-button class="mr-2" type="primary" @click="setWatermark('WaterMark Info')">
        Create
      </a-button>
      <a-button class="mr-2" color="error" @click="clear"> Clear </a-button>
      <a-button class="mr-2" color="warning" @click="setWatermark('WaterMark Info New')">
        Reset
      </a-button>
    </CollapseContainer>
  </PageWrapper>
</template>
<script lang="ts">
  import { defineComponent, ref } from 'vue';
  import { CollapseContainer } from '/@/components/Container/index';
  import { useWatermark } from '/@/hooks/web/useWatermark';
  import { PageWrapper } from '/@/components/Page';

  export default defineComponent({
    components: { CollapseContainer, PageWrapper },
    setup() {
      const areaRef = ref<Nullable<HTMLElement>>(null);
      const { setWatermark, clear } = useWatermark();
      return {
        setWatermark,
        clear,
        areaRef,
      };
    },
  });
</script>
