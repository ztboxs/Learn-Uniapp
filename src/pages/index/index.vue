<script setup lang="ts">
//自定义导航栏
import { getHomeBannerAPI } from '@/services/home'
import type { BannerItem } from '@/types/home'
import { onLoad } from '@dcloudio/uni-app'
import { ref } from 'vue'
import CustomNavbar from './components/CustomNavbar.vue'

// 获取轮播图数据
const bannerList = ref<BannerItem[]>([])
const getHomeBannerData = async () => {
  const res = await getHomeBannerAPI()
  bannerList.value = res.result
}

// 页面加载
onLoad(async () => {
  getHomeBannerData()
})
</script>

<template>
  <!-- 自定义导航栏 -->
  <CustomNavbar />
  <!-- 自定义轮播图 -->
  <XtxSwiper :list="bannerList" />
  <text>index</text>
</template>

<style lang="scss">
//
</style>
