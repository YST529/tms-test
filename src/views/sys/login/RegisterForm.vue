<template>
  <template v-if="getShow">
    <LoginFormTitle class="enter-x" />
    <Form ref="formRef" :model="formData" :rules="getFormRules" class="p-4 enter-x">
      <FormItem class="enter-x" name="account">
        <Input
          v-model:value="formData.account"
          :placeholder="t('sys.login.userName')"
          class="fix-auto-fill"
          size="large"
        />
      </FormItem>
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
      <FormItem class="enter-x" name="password">
        <StrengthMeter
          v-model:value="formData.password"
          :placeholder="t('sys.login.password')"
          size="large"
        />
      </FormItem>
      <FormItem class="enter-x" name="confirmPassword">
        <InputPassword
          v-model:value="formData.confirmPassword"
          :placeholder="t('sys.login.confirmPassword')"
          size="large"
          visibilityToggle
        />
      </FormItem>

      <FormItem class="enter-x" name="policy">
        <!-- No logic, you need to deal with it yourself -->
        <Checkbox v-model:checked="formData.policy" size="small">
          {{ t('sys.login.policy') }}
        </Checkbox>
      </FormItem>

      <Button
        :loading="loading"
        block
        class="enter-x"
        size="large"
        type="primary"
        @click="handleRegister"
      >
        {{ t('sys.login.registerButton') }}
      </Button>
      <Button block class="mt-4 enter-x" size="large" @click="handleBackLogin">
        {{ t('sys.login.backSignIn') }}
      </Button>
    </Form>
  </template>
</template>
<script lang="ts" setup>
  import { reactive, ref, unref, computed } from 'vue';
  import LoginFormTitle from './LoginFormTitle.vue';
  import { Form, Input, Button, Checkbox } from 'ant-design-vue';
  import { StrengthMeter } from '/@/components/StrengthMeter';
  import { CountdownInput } from '/@/components/CountDown';
  import { useI18n } from '/@/hooks/web/useI18n';
  import { useLoginState, useFormRules, useFormValid, LoginStateEnum } from './useLogin';

  const FormItem = Form.Item;
  const InputPassword = Input.Password;
  const { t } = useI18n();
  const { handleBackLogin, getLoginState } = useLoginState();

  const formRef = ref();
  const loading = ref(false);

  const formData = reactive({
    account: '',
    password: '',
    confirmPassword: '',
    mobile: '',
    sms: '',
    policy: false,
  });

  const { getFormRules } = useFormRules(formData);
  const { validForm } = useFormValid(formRef);

  const getShow = computed(() => unref(getLoginState) === LoginStateEnum.REGISTER);

  async function handleRegister() {
    const data = await validForm();
    if (!data) return;
    console.log(data);
  }
</script>
