<template>
  <view>
    <wd-search class="search" v-model="search_value" @cancel="search" @search="search" placeholder="请输入要搜索的内容"  maxlength="10" placeholder-left cancel-txt="搜索" />
    <wd-swiper class="advertise" :list="advertise_list" autoplay v-model:current="current" @click="handleClick"></wd-swiper>
    <wd-grid clickable :column="6">
      <wd-grid-item icon="/static/icon/fruit.png" @itemclick="buy_click('fruit')" text="蔬菜水果" />
      <wd-grid-item icon="/static/icon/oil.png" @itemclick="buy_click('oil')" text="粮油副食" />
      <wd-grid-item icon="/static/icon/meat.png" @itemclick="buy_click('meat')" text="肉禽蛋奶" />
      <wd-grid-item icon="/static/icon/seafood.png" @itemclick="buy_click('seafood')" text="水产海鲜" />
      <wd-grid-item icon="/static/icon/p_agricultural.png" @itemclick="buy_click('p_agricultural')" text="加工农产品" />
      <wd-grid-item icon="/static/icon/s_agricultural.png" @itemclick="buy_click('s_agricultural')" text="特色农产品" />
    </wd-grid>
    <wd-grid clickable :column="3">
      <wd-grid-item icon="/static/icon/farmer.png" @itemclick="storyclick('farmer')"text="农民奋斗故事" />
      <wd-grid-item icon="/static/icon/skill.png" @itemclick="storyclick('farmer')" text="技艺传承故事" :icon-style="{ width: '50px', height: '50px', 'object-fit': 'contain' }"/>
      <wd-grid-item icon="/static/icon/return_home.png" @itemclick="storyclick('farmer')" text="返乡创业故事" />
      <wd-grid-item icon="/static/icon/region.png" @itemclick="storyclick('farmer')" text="地域特色故事" />
      <wd-grid-item icon="/static/icon/nationality.png" @itemclick="storyclick('farmer')" text="民族风味故事" />
      <wd-grid-item icon="/static/icon/return_home2.png" @itemclick="storyclick('farmer')" text="返乡创业其他" />
    </wd-grid>
    <wd-grid :column="4">
      <wd-grid-item icon="/static/icon/hotel.png" text="土地认领" />
      <wd-grid-item icon="/static/icon/transportation.png" text="果园认领" :icon-style="{ width: '50px', height: '50px', 'object-fit': 'contain' }"/>
      <wd-grid-item icon="/static/icon/food.png" text="咨询动态" />
      <wd-grid-item icon="/static/icon/play.png" text="我的认领" />
    </wd-grid>
    <view>
      <wd-card title="经营分析">
      一般的，检举内容由承办的党的委员会或纪律检查委员会将处理意见或复议、复查结论同申诉人见面，听取其意见。复议、复查的结论和决定，应交给申诉人一份。
      <template #footer>
        <wd-button size="small" plain>查看详情</wd-button>
      </template>
    </wd-card>
    </view>
    <tabbar></tabbar>
  </view>
</template>

<script setup>
import { ref } from 'vue'

let search_value = ref("")
let current = ref(0)
let advertise_list = ref([
  'https://registry.npmmirror.com/wot-design-uni-assets/*/files/redpanda.jpg',
  'https://registry.npmmirror.com/wot-design-uni-assets/*/files/capybara.jpg',
  'https://registry.npmmirror.com/wot-design-uni-assets/*/files/panda.jpg',
  'https://registry.npmmirror.com/wot-design-uni-assets/*/files/moon.jpg',
  'https://registry.npmmirror.com/wot-design-uni-assets/*/files/meng.jpg'
])

//摁下故事板块
function storyclick()
{
  console.log(1)
  uni.navigateTo({url: '/pages/storys/storys'});
}
//wd-swiper被摁下
function handleClick(e) 
{
  console.log(current.value)
}

//搜索框搜索方法
function search(e)
{
  console.log(search_value.value)
}


</script>

<style>
.advertise{
  margin-left: 10px;
  margin-right: 10px;
}

</style>
