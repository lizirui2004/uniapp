<template>
  <view class="container">
    <!-- Logo 居中 -->
    <view class="logo-container">
      <image class="logo" src="/static/logo.png" mode="aspectFit"></image>
    </view>
    <!-- 登录表单 -->
    <form action="">
      <view class="form-container">
          <!-- 账号密码 -->
            <wd-input class="input" style="margin-bottom: 20px;" type="text" v-model="value" placeholder="用户名" @change="handleChange" />
            <wd-input class="input" type="text" v-model="value" placeholder="密码" @change="handleChange" />
            <wd-row style="width: 80%;margin-bottom: 40px;">
              <wd-col :span="12"><navigator style=" font-size: 10px; color: #A9A9A9;" url="/pages/" open-type="navigate" hover-class="navigator-hover">注册账号</navigator></wd-col>
              <wd-col :span="12"><view class="bg-light"></view></wd-col>
              <wd-col :span="12"> <navigator style=" float: right; font-size: 10px; color: #A9A9A9;" url="/pages/" open-type="navigate" hover-class="navigator-hover">忘记密码</navigator></wd-col>
            </wd-row>      
            <wd-button class="login-button" style="margin-bottom: 40px;" @click="login">登录</wd-button>
            <wd-checkbox v-model="value" @change="handleChange">我已阅读并同意<navigator style="display: inline-block; color: #6dc0e4;">用户隐私政策</navigator>和<navigator style="display: inline-block; color: #6dc0e4;">用户服务协议</navigator></wd-checkbox>
      </view>
    </form>
  </view>
</template>

<script setup>
function login()
{
  uni.redirectTo({ url: '/pages/index/index' })
}
</script>

<style>

/* 页面容器 */
.container {
padding: 20px;
height: 100vh;
background-color: #f5f5f5;
}

/* Logo 容器 */
.logo-container {
display: flex;
justify-content: center;
align-items: center;
width: 100%;
margin-top: 30px;
}

/* Logo 图片 */
.logo {
width: 150px;
height: 150px;
}

/* 表单容器 */
.form-container {
display: flex;
flex-direction: column; /* 竖向排列 */
align-items: center; /* 水平居中 */
width: 100%;
margin-top: 20px;
}
/* 输入框样式 */
.input {
width: 85%;
font-size: 40px;
}

/* 登录按钮样式 */
.login-button {
width: 30%;
height: 40px;
font-size: 20px;
}

</style>