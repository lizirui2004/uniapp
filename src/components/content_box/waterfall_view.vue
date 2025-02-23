<template>
  <waterfall column-count="2" column-width="auto">
    <cell v-for="(num,index) in lists" >
      <image
        :src= "advertise_list[index]"
        mode="scaleToFill"
      />
      <text>{{num}}</text>
    </cell>
  </waterfall>
</template>
<script setup>
import { ref } from 'vue'
let advertise_list = ref([
  'https://registry.npmmirror.com/wot-design-uni-assets/*/files/redpanda.jpg',
  'https://registry.npmmirror.com/wot-design-uni-assets/*/files/capybara.jpg',
  'https://registry.npmmirror.com/wot-design-uni-assets/*/files/panda.jpg',
  'https://registry.npmmirror.com/wot-design-uni-assets/*/files/moon.jpg',
  'https://registry.npmmirror.com/wot-design-uni-assets/*/files/meng.jpg'
])

let lists = ref(['redpanda','capybara','panda.jpg','moon.jpg','meng.jpg'])
</script>

<style></style>