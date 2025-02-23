<template>
    <wd-card v-for="(item,index) in items" :title="aaa">
    <view style="height: 40px;" class="content">
      <image :src="item.img" alt="joy"style="border-radius: 4px; margin-right: 12px;width: 40px;height: 40px;"/>
      <view>
        <view  style="color: rgba(0,0,0,0.85); font-size: 16px;">{{ item.title }}</view>
        <view class="ellipsis" style="color: rgba(0,0,0,0.25); font-size: 12px;">{{ item.content }}</view>
      </view>
    </view>
    
    <template #footer>
        <wd-button size="small" plain>查看详情</wd-button>
    </template>
</wd-card>
</template>
<script setup>
import { ref } from 'vue'
let items=[
    {
        title:"老张的坚持",
        img:"https://img11.360buyimg.com/imagetools/jfs/t1/143248/37/5695/265818/5f3a8546E98d998a4/745897ca9c9e474b.jpg",
        content:"老张家里只有一块地，耕作条件不好，但他每年都坚持种植。即使收成不好，他也从不放弃，总是精心照料每一颗庄稼。邻居劝他换地或者转行，但老张始终坚信只要坚持，总会有收获。几年后，他的地得到了改善，土地变得肥沃，收成逐年增多，成为了村里有名的“富农”。邻居们都佩服他：坚持与耐心，最终带来了回报。"
    },
    {
        title:"小王的创新",
        img:"https://img11.360buyimg.com/imagetools/jfs/t1/143248/37/5695/265818/5f3a8546E98d998a4/745897ca9c9e474b.jpg",
        content:"小王继承了父亲的农田，但传统的耕作方法已经不能满足现代需求。于是，他决定尝试引进现代化的农业技术，学习精细化管理和科学施肥。刚开始，许多村民都嘲笑他，但他依然坚定实践自己的想法。几年后，小王的农田产量翻了几倍，他的成功让村里其他农民纷纷效仿，大家的生活逐渐富裕起来。"
    }
]
</script>
<style>
.content,
.title {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
}
.content {
  justify-content: flex-start;
}
.ellipsis {
  width: 200px; /* 限制宽度 */
  height: 40px;
  overflow: hidden; /* 隐藏超出的部分 */
  text-overflow: ellipsis; /* 超出部分用省略号表示 */
}
</style>