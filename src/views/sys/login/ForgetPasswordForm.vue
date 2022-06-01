<template>
  <template v-if="getShow">
    <LoginFormTitle class="enter-x" />
    <Form ref="formRef" :model="formData" :rules="getFormRules" class="p-4 enter-x">
      <FormItem class="enter-x" name="account">
        <Input
          v-model:value="formData.account"
          :placeholder="t('sys.login.userName')"
          size="large"
        />
      </FormItem>

      <FormItem class="enter-x" name="mobile">
        <Input v-model:value="formData.mobile" :placeholder="t('sys.login.mobile')" size="large" />
      </FormItem>
      <FormItem class="enter-x" name="sms">
        <CountdownInput
          v-model:value="formData.sms"
          :placeholder="t('sys.login.smsCode')"
          size="large"
        />
      </FormItem>

      <FormItem class="enter-x">
        <Button :loading="loading" block size="large" type="primary" @click="handleReset">
          {{ t('common.resetText') }}
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
  import LoginFormTitle from './LoginFormTitle.vue';
  import { Form, Input, Button } from 'ant-design-vue';
  import { CountdownInput } from '/@/components/CountDown';
  import { useI18n } from '/@/hooks/web/useI18n';
  import { useLoginState, useFormRules, LoginStateEnum } from './useLogin';

  const FormItem = Form.Item;
  const { t } = useI18n();
  const { handleBackLogin, getLoginState } = useLoginState();
  const { getFormRules } = useFormRules();

  const formRef = ref();
  const loading = ref(false);

  const formData = reactive({
    account: '',
    mobile: '',
    sms: '',
  });

  const getShow = computed(() => unref(getLoginState) === LoginStateEnum.RESET_PASSWORD);

  async function handleReset() {
    const form = unref(formRef);
    if (!form) return;
    await form.resetFields();
  }
</script>
