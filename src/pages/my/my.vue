<template>
  <view class="container">
    <!-- 头部用户信息 -->
    <view class="user-info">
      <image class="avatar" src="/static/avatar.jpg"></image>
      <text class="username">用户名</text>
    </view>

    <!-- 积分和红包卡券 -->
    <view class="points-coupons">
      <view class="item">
        <text class="label">e购积分</text>
        <text class="value">1000</text>
      </view>
      <view class="item">
        <text class="label">红包卡券</text>
        <text class="value">5张</text>
      </view>
    </view>
    <wd-grid clickable :column="5">
      <wd-grid-item icon="/static/icon-pay.png" @itemclick="storyclick('farmer')"text="待付款" />
      <wd-grid-item icon="/static/icon-ship.png" @itemclick="storyclick('farmer')" text="待出行" :icon-style="{ width: '50px', height: '50px', 'object-fit': 'contain' }"/>
      <wd-grid-item icon="/static/icon-comment.png" @itemclick="storyclick('farmer')" text="待评价" />
      <wd-grid-item icon="/static/icon-after-sale.png" @itemclick="storyclick('farmer')" text="售后" />
      <wd-grid-item icon="/static/icon-all-orders.png" @itemclick="storyclick('farmer')" text="全部订单" />
    </wd-grid>
    <!-- 订单状态 -->

    <wd-grid clickable :column="4">
      <wd-grid-item icon="/static/icon-favorite.png" @itemclick="storyclick('farmer')"text="我的收藏" />
      <wd-grid-item icon="/static/icon-cart.png" @itemclick="storyclick('farmer')" text="购物车" :icon-style="{ width: '50px', height: '50px', 'object-fit': 'contain' }"/>
      <wd-grid-item icon="/static/icon-history.png" @itemclick="storyclick('farmer')" text="历史记录" />
      <wd-grid-item icon="/static/icon-info.png" @itemclick="storyclick('farmer')" text="常用信息" />
    </wd-grid>
    <!-- 我的收藏、购物车、历史记录、常用信息 -->

    <!-- 我的旅行会议 -->
    <view class="travel-meetings">
      <view class="meeting-item" v-for="(item, index) in meetings" :key="index">
        <image class="meeting-image" :src="item.image"></image>
        <text class="meeting-title">{{ item.title }}</text>
      </view>
    </view>
  </view>
  <tabbar></tabbar>
</template>

<script>
export default {
  data() {
    return {
      meetings: [
        { image: '/static/meeting1.jpg', title: '旅行回忆1' },
        { image: '/static/meeting2.jpg', title: '旅行回忆2' },
        { image: '/static/meeting3.jpg', title: '旅行回忆3' },
      ]
    };
  }
};
</script>

<style>
.container {
  padding: 20px;
}

.user-info {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.avatar {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  margin-right: 10px;
}

.username {
  font-size: 18px;
  font-weight: bold;
}

.points-coupons {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

.item {
  text-align: center;
}

.label {
  font-size: 14px;
  color: #666;
}

.value {
  font-size: 18px;
  font-weight: bold;
}

.order-status {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

.status-item {
  text-align: center;
}

.icon {
  width: 30px;
  height: 30px;
  margin-bottom: 5px;
}

.text {
  font-size: 14px;
  color: #666;
}

.my-links {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

.link-item {
  text-align: center;
}

.travel-meetings {
  display: flex;
  flex-direction: column;
}

.meeting-item {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.meeting-image {
  width: 80px;
  height: 80px;
  border-radius: 10px;
  margin-right: 10px;
}

.meeting-title {
  font-size: 16px;
  font-weight: bold;
}
</style>