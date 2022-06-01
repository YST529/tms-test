<template>
  <template v-if="getShow">
    <LoginFormTitle class="enter-x" />
    <Form ref="formRef" :model="formData" :rules="getFormRules" class="p-4 enter-x">
      <FormItem class="enter-x" name="mobile">
        <Input
          v-model:value="formData.mobile"
          :placeholder="t('sys.login.mobile')"
          class="fix-auto-fill"
          size="large"
        />
      </FormItem>
      <FormItem class="enter-x" name="sms">
        <CountdownInput
          v-model:value="formData.sms"
          :placeholder="t('sys.login.smsCode')"
          class="fix-auto-fill"
          size="large"
        />
      </FormItem>

      <FormItem class="enter-x">
        <Button :loading="loading" block size="large" type="primary" @click="handleLogin">
          {{ t('sys.login.loginButton') }}
        </Button>
        <Button block class="mt-4" size="large" @click="handleBackLogin">
          {{ t('sys.login.backSignIn') }}
        </Button>
      </FormItem>
    </Form>
  </template>
</template>
<script lang="ts" setup>
  import { reactive, ref, computed, unref } from 'vue';
  import { Form, Input, Button } from 'ant-design-vue';
  import { CountdownInput } from '/@/components/CountDown';
  import LoginFormTitle from './LoginFormTitle.vue';
  import { useI18n } from '/@/hooks/web/useI18n';
  import { useLoginState, useFormRules, useFormValid, LoginStateEnum } from './useLogin';

  const FormItem = Form.Item;
  const { t } = useI18n();
  const { handleBackLogin, getLoginState } = useLoginState();
  const { getFormRules } = useFormRules();

  const formRef = ref();
  const loading = ref(false);

  const formData = reactive({
    mobile: '',
    sms: '',
  });

  const { validForm } = useFormValid(formRef);

  const getShow = computed(() => unref(getLoginState) === LoginStateEnum.MOBILE);

  async function handleLogin() {
    const data = await validForm();
    if (!data) return;
    console.log(data);
  }
</script>
