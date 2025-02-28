<template>
  <view class="chat-list-page">
    <!-- 顶部标题栏 -->
    <view class="top-bar">
      <view class="title">聊天</view>
    </view>

    <!-- 聊天列表 -->
    <scroll-view class="chat-list" scroll-y>
      <view
        v-for="(item, index) in chatList"
        :key="index"
        class="chat-item"
        @click="goToChatDetail(item)"
      >
        <!-- 头像 -->
        <image class="avatar" :src="item.avatar"></image>

        <!-- 聊天内容 -->
        <view class="content">
          <!-- 用户名和最后一条消息 -->
          <view class="info">
            <view class="username">{{ item.username }}</view>
            <view class="last-message">{{ item.lastMessage }}</view>
          </view>

          <!-- 时间和未读消息 -->
          <view class="meta">
            <view class="time">{{ item.time }}</view>
            <view v-if="item.unreadCount > 0" class="unread-count">
              {{ item.unreadCount }}
            </view>
          </view>
        </view>
      </view>
    </scroll-view>
  </view>
  <tabbar></tabbar>
</template>

<script>
export default {
  data() {
    return {
      // 聊天列表数据
      chatList: [
        {
          id: 1,
          username: "张三",
          avatar: "/static/avatars/user1.jpg",
          lastMessage: "你好，最近怎么样？",
          time: "10:30",
          unreadCount: 2,
        },
        {
          id: 2,
          username: "李四",
          avatar: "/static/avatars/user2.jpg",
          lastMessage: "晚上一起吃饭吗？",
          time: "昨天",
          unreadCount: 0,
        },
        {
          id: 3,
          username: "王五",
          avatar: "/static/avatars/user3.jpg",
          lastMessage: "好的，没问题！",
          time: "前天",
          unreadCount: 5,
        },
      ],
    };
  },
  methods: {
    // 跳转到聊天详情页
    goToChatDetail(item) {
      uni.navigateTo({
        url: `/pages/chat/chat-detail?id=${item.id}&username=${item.username}`,
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.chat-list-page {
  height: 100vh;
  background-color: #f5f5f5;

  .top-bar {
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #ffffff;
    border-bottom: 1px solid #e5e5e5;

    .title {
      font-size: 18px;
      font-weight: bold;
    }
  }

  .chat-list {
    height: calc(100vh - 60px);
    padding: 10px;

    .chat-item {
      display: flex;
      align-items: center;
      padding: 10px;
      background-color: #ffffff;
      border-radius: 8px;
      margin-bottom: 10px;

      .avatar {
        width: 50px;
        height: 50px;
        border-radius: 50%;
        margin-right: 10px;
      }

      .content {
        flex: 1;
        display: flex;
        justify-content: space-between;
        align-items: center;

        .info {
          .username {
            font-size: 16px;
            font-weight: bold;
            margin-bottom: 5px;
          }

          .last-message {
            font-size: 14px;
            color: #666666;
          }
        }

        .meta {
          text-align: right;

          .time {
            font-size: 12px;
            color: #999999;
            margin-bottom: 5px;
          }

          .unread-count {
            display: inline-block;
            padding: 2px 6px;
            background-color: #ff4444;
            color: #ffffff;
            font-size: 12px;
            border-radius: 10px;
          }
        }
      }
    }
  }
}
</style>