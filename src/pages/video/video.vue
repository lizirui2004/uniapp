<template>
  <view class="page">
    <swiper
      class="card-swiper"
      :circular="true"
      vertical="true"
      :autoplay="true"
      duration="500"
      interval="5000"
      @change="cardSwiper"
    >
      <swiper-item
        v-for="(item, index) in swiperList"
        :key="index"
        :class="cardCur == index ? 'cur' : ''"
      >
        <view class="swiper-item image-banner">
          <video
            :id="`video-${item.id}`"
            :src="item.mp4"
            loop
            style="height: 100vh; width: 100vw; object-fit: cover;"
          ></video>
          <!-- 操作栏 -->
          <view class="action-bar">
            <view class="action-item" @click="handleLike(item.id)">
              <text class="icon">👍</text>
              <text>{{ item.likes || 0 }}</text>
            </view>
            <view class="action-item" @click="handleCollect(item.id)">
              <text class="icon">❤️</text>
              <text>{{ item.collects || 0 }}</text>
            </view>
            <view class="action-item" @click="handleComment(item.id)">
              <text class="icon">💬</text>
              <text>{{ item.comments || 0 }}</text>
            </view>
          </view>
        </view>
      </swiper-item>
    </swiper>
  </view>
  <tabbar class="tabbar"></tabbar>
</template>

<script>
export default {
  data() {
    return {
      cardCur: 0,
      swiperList: [
        {
          id: 0,
          mp4: "/static/testvideo/1.mp4",
          likes: 0, // 点赞数
          collects: 0, // 收藏数
          comments: 0, // 评论数
        },
        {
          id: 1,
          mp4: "/static/testvideo/1.mp4",
          likes: 0,
          collects: 0,
          comments: 0,
        },
        {
          id: 2,
          mp4: "/static/testvideo/1.mp4",
          likes: 0,
          collects: 0,
          comments: 0,
        },
      ],
    };
  },
  methods: {
    cardSwiper(e) {
      this.cardCur = e.detail.current;
      for (let i = 0; i < this.swiperList.length; i++) {
        const videoContext = uni.createVideoContext(
          `video-${this.swiperList[i]["id"]}`,
          this
        );
        if (i === this.cardCur) {
          videoContext.play();
        } else {
          videoContext.stop();
        }
      }
    },
    // 点赞
    handleLike(id) {
      const item = this.swiperList.find((item) => item.id === id);
      if (item) {
        item.likes += 1;
        uni.showToast({
          title: "点赞成功",
          icon: "none",
        });
      }
    },
    // 收藏
    handleCollect(id) {
      const item = this.swiperList.find((item) => item.id === id);
      if (item) {
        item.collects += 1;
        uni.showToast({
          title: "收藏成功",
          icon: "none",
        });
      }
    },
    // 评论
    handleComment(id) {
      uni.showModal({
        title: "评论",
        placeholderText: "请输入评论内容",
        success: (res) => {
          if (res.confirm && res.content) {
            const item = this.swiperList.find((item) => item.id === id);
            if (item) {
              item.comments += 1;
              uni.showToast({
                title: "评论成功",
                icon: "none",
              });
            }
          }
        },
      });
    },
  },
};
</script>

<style>
/* 页面样式 */
.page {
  overflow: hidden; /* 禁用页面滚动 */
  width: 100vw;
  height: 100vh; /* 占满视口高度 */
  background-color: #000; /* 设置背景色为黑色，避免白边 */
}

/* Swiper 样式 */
.card-swiper {
  height: 93%; /* 占满视口高度 */
}

.card-swiper swiper-item {
  width: 100vw !important; /* 占满视口宽度 */
  height: auto; /* 占满视口高度 */
  box-sizing: border-box;
  overflow: hidden; /* 隐藏溢出内容 */
}

.card-swiper swiper-item .swiper-item {
  width: 100%;
  height: auto; /* 占满视口高度 */
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative; /* 相对定位 */
}

/* 视频样式 */
video {
  width: 100vw; /* 占满视口宽度 */
  height: auto; /* 占满视口高度 */
  object-fit: cover; /* 视频填充容器，避免变形 */
}

/* 操作栏样式 */
.action-bar {
  position: absolute;
  bottom: 15%;
  right: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.action-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #fff;
  font-size: 14px;
}

.action-item .icon {
  font-size: 24px;
}
</style>