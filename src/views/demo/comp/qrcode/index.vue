<template>
  <PageWrapper title="二维码组件使用示例">
    <div class="flex flex-wrap">
      <CollapseContainer
        :canExpan="true"
        class="text-center mb-6 qrcode-demo-item"
        title="基础示例"
      >
        <QrCode :value="qrCodeUrl" />
      </CollapseContainer>

      <CollapseContainer class="text-center mb-6 qrcode-demo-item" title="渲染成img标签示例">
        <QrCode :value="qrCodeUrl" tag="img" />
      </CollapseContainer>

      <CollapseContainer class="text-center mb-6 qrcode-demo-item" title="配置样式示例">
        <QrCode
          :options="{
            color: { dark: '#55D187' },
          }"
          :value="qrCodeUrl"
        />
      </CollapseContainer>

      <CollapseContainer class="text-center mb-6 qrcode-demo-item" title="本地logo示例">
        <QrCode :logo="LogoImg" :value="qrCodeUrl" />
      </CollapseContainer>

      <CollapseContainer class="text-center mb-6 qrcode-demo-item" title="在线logo示例">
        <QrCode
          :options="{
            color: { dark: '#55D187' },
          }"
          :value="qrCodeUrl"
          logo="https://vebn.oss-cn-beijing.aliyuncs.com/vben/logo.png"
        />
      </CollapseContainer>

      <CollapseContainer class="text-center mb-6 qrcode-demo-item" title="logo配置示例">
        <QrCode
          :logo="{
            src: 'https://vebn.oss-cn-beijing.aliyuncs.com/vben/logo.png',
            logoSize: 0.2,
            borderSize: 0.05,
            borderRadius: 50,
            bgColor: 'blue',
          }"
          :value="qrCodeUrl"
        />
      </CollapseContainer>

      <CollapseContainer class="text-center qrcode-demo-item" title="下载示例">
        <QrCode ref="qrRef" :logo="LogoImg" :value="qrCodeUrl" />
        <a-button class="mb-2" type="primary" @click="download"> 下载 </a-button>
        <div class="msg">(在线logo会导致图片跨域，需要下载图片需要自行解决跨域问题)</div>
      </CollapseContainer>

      <CollapseContainer class="text-center qrcode-demo-item" title="配置大小示例">
        <QrCode :value="qrCodeUrl" :width="300" />
      </CollapseContainer>

      <CollapseContainer class="text-center qrcode-demo-item" title="扩展绘制示例">
        <QrCode
          ref="qrDiyRef"
          :logo="LogoImg"
          :options="{ margin: 5 }"
          :value="qrCodeUrl"
          :width="200"
          @done="onQrcodeDone"
        />
        <a-button class="mb-2" type="primary" @click="downloadDiy"> 下载 </a-button>
        <div class="msg">要进行扩展绘制则不能将tag设为img</div>
      </CollapseContainer>
    </div>
  </PageWrapper>
</template>
<script lang="ts">
  import { defineComponent, ref, unref } from 'vue';
  import { QrCode, QrCodeActionType } from '/@/components/Qrcode/index';
  import LogoImg from '/@/assets/images/logo.png';
  import { CollapseContainer } from '/@/components/Container/index';
  import { PageWrapper } from '/@/components/Page';

  const qrCodeUrl = 'https://www.vvbin.cn';
  export default defineComponent({
    components: { CollapseContainer, QrCode, PageWrapper },
    setup() {
      const qrRef = ref<Nullable<QrCodeActionType>>(null);
      const qrDiyRef = ref<Nullable<QrCodeActionType>>(null);
      function download() {
        const qrEl = unref(qrRef);
        if (!qrEl) return;
        qrEl.download('文件名');
      }
      function downloadDiy() {
        const qrEl = unref(qrDiyRef);
        if (!qrEl) return;
        qrEl.download('Qrcode');
      }

      function onQrcodeDone({ ctx }: any) {
        if (ctx instanceof CanvasRenderingContext2D) {
          // 额外绘制
          ctx.fillStyle = 'black';
          ctx.font = '16px "微软雅黑"';
          ctx.textBaseline = 'bottom';
          ctx.textAlign = 'center';
          ctx.fillText('你帅你先扫', 100, 195, 200);
        }
      }
      return {
        onQrcodeDone,
        qrCodeUrl,
        LogoImg,
        download,
        downloadDiy,
        qrRef,
        qrDiyRef,
      };
    },
  });
</script>
<style scoped>
  .qrcode-demo-item {
    width: 30%;
    margin-right: 1%;
  }
</style>
