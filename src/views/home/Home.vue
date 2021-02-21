<template>
  <div id="home">
    <nav-bar class="nav-bar">
      <div slot="center">购物车</div>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar"
import HomeSwiper from "@/components/content/swiper/HomeSwiper"

import {getHomeMultiData} from "@/network/home"

export default {
  name: "Home",
  components: {
    NavBar,
    HomeSwiper
  },
  data() {
    return {
      banners: [],
      recommends: []
    }
  },
  created () {
    getHomeMultiData().then(res => {
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    })
  },
}
</script>

<style>
 .nav-bar{
   background-color: var(--color-tint);
   color: #fff;
 }
</style>