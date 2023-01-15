<template>
    <div class="login-box">
        <a-form layout="horizontal" ref="formRef" :model="state.formInline" @submit.prevent="submit">
            <a-form-item>
                <a-input allow-clear placeholder="用户名" v-model:value="state.formInline.username" size="large">
                    <template #prefix>
                        <user-outlined type="user" />
                    </template>
                </a-input>
            </a-form-item>
            <a-form-item>
                <a-input-password placeholder="请输入密码" v-model:value="state.formInline.password" size="large">
                    <template #prefix><lock-outlined type="user" /></template>
                </a-input-password>
            </a-form-item>
            <a-form-item>
                <a-input placeholder="验证码" v-model:value="state.formInline.verifyCode" size="large">
                    <template #prefix>
                        <SafetyOutlined />
                    </template>
                    <template #suffix>
                        <img :src="state.captcha" class="absolute right-0 h-full cursor-pointer" @click="setCaptcha" />
                    </template>
                </a-input>
            </a-form-item>
            <a-form-item>
                <a-button type="primary" html-type="submit" size="large" block>登录</a-button>
            </a-form-item>
        </a-form>
    </div>
</template>

<script lang="ts" setup>
import { ref, reactive, toRefs, onMounted, getCurrentInstance, computed } from 'vue'
import { UserOutlined, LockOutlined, SafetyOutlined } from '@ant-design/icons-vue'

const state = reactive({
    loading: false,
    captcha: "",
    formInline: {
        username: '',
        password: '',
        verifyCode: '',
        captchaId: ''
    }
})

// 获取检验图片
const setCaptcha = async () => {

}

const submit = () => {
    console.log('提交')
}
</script>

<style scoped lang="less">
:deep(.ant-form) {
    width: 400px;

    .ant-col {
        width: 100%;
    }

    .ant-form-item-label {
        padding-right: 6px;
    }
}
</style>