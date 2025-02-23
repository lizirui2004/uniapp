<template>
  <wd-tabbar fixed shape="round" v-model="activeTab" @change="handleTabChange" bordered safeAreaInsetBottom >
    <wd-tabbar-item title="首页" icon="home" label="首页"></wd-tabbar-item>
    <wd-tabbar-item title="小视频" icon="play-circle-filled" label="小视频"></wd-tabbar-item>
    <wd-tabbar-item title="AI" icon="user" label="AI"></wd-tabbar-item>
    <wd-tabbar-item title="消息" icon="user" label="消息"></wd-tabbar-item>
    <wd-tabbar-item title="我的" icon="user" label="我的"></wd-tabbar-item>
  </wd-tabbar>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// 定义响应式变量
const activeTab = ref(0)

// 定义 tabPage 列表
const tabPage = ["/pages/index/index", "/pages/video/video" ,"/pages/AI/AI", "/pages/message/message", "/pages/my/my"]

// 更新 activeTab 的方法
function updateActiveTab() {
  const currentPage = getCurrentPages();
  const currentRoute = currentPage[currentPage.length - 1].route;  // 获取当前页面的路径

  const index = tabPage.indexOf("/" + currentRoute);  // 查找当前路径对应的 tabbar 索引
  if (index !== -1) {
    activeTab.value = index;  // 更新 activeTab
  }
}

// 切换 tab 页
function handleTabChange() {
  uni.redirectTo({ url: tabPage[activeTab.value] });
}

// 页面加载时判断当前页面并更新 activeTab
onMounted(() => {
  updateActiveTab();
});

// 监听页面切换
uni.$on('routeChange', () => {
  updateActiveTab();
});
</script>