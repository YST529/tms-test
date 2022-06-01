<template>
  <PageWrapper content="需要开启测试接口服务才能进行上传测试！" title="图片裁剪示例">
    <CollapseContainer title="头像裁剪">
      <CropperAvatar :uploadApi="uploadApi" :value="avatar" />
    </CollapseContainer>

    <CollapseContainer class="my-4" title="矩形裁剪">
      <div class="container p-4">
        <div class="cropper-container mr-10">
          <CropperImage ref="refCropper" :src="img" style="width: 40vw" @cropend="handleCropend" />
        </div>
        <img v-if="cropperImg" :src="cropperImg" alt="" class="croppered" />
      </div>
      <p v-if="cropperImg">裁剪后图片信息：{{ info }}</p>
    </CollapseContainer>

    <CollapseContainer title="圆形裁剪">
      <div class="container p-4">
        <div class="cropper-container mr-10">
          <CropperImage
            ref="refCropper"
            :src="img"
            circled
            style="width: 40vw"
            @cropend="handleCircleCropend"
          />
        </div>
        <img v-if="circleImg" :src="circleImg" class="croppered" />
      </div>
      <p v-if="circleImg">裁剪后图片信息：{{ circleInfo }}</p>
    </CollapseContainer>
  </PageWrapper>
</template>
<script lang="ts">
  import { defineComponent, ref } from 'vue';
  import { PageWrapper } from '/@/components/Page';
  import { CollapseContainer } from '/@/components/Container';
  import { CropperImage, CropperAvatar } from '/@/components/Cropper';
  import { uploadApi } from '/@/api/sys/upload';
  import img from '/@/assets/images/header.jpg';
  import { useUserStore } from '/@/store/modules/user';

  export default defineComponent({
    components: {
      PageWrapper,
      CropperImage,
      CollapseContainer,
      CropperAvatar,
    },
    setup() {
      const info = ref('');
      const cropperImg = ref('');
      const circleInfo = ref('');
      const circleImg = ref('');
      const userStore = useUserStore();
      const avatar = ref(userStore.getUserInfo?.avatar || '');
      function handleCropend({ imgBase64, imgInfo }) {
        info.value = imgInfo;
        cropperImg.value = imgBase64;
      }

      function handleCircleCropend({ imgBase64, imgInfo }) {
        circleInfo.value = imgInfo;
        circleImg.value = imgBase64;
      }

      return {
        img,
        info,
        circleInfo,
        cropperImg,
        circleImg,
        handleCropend,
        handleCircleCropend,
        avatar,
        uploadApi: uploadApi as any,
      };
    },
  });
</script>

<style scoped>
  .container {
    display: flex;
    width: 100vw;
    align-items: center;
  }

  .cropper-container {
    width: 40vw;
  }

  .croppered {
    height: 360px;
  }

  p {
    margin: 10px;
  }
</style>
