<template>
  <div id="home">
    <nav-bar class="nav-bar">
      <div slot="center">购物车</div>
    </nav-bar>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar"
import {getHomeMultiData} from "@/network/home"

export default {
  name: "Home",
  components: {
    NavBar,
  },
  data() {
    return {
      banner: null,
      recommend: null
    }
  },
  created () {
    getHomeMultiData().then(res => {
      this.banner = res.data.banner.list;
      this.recommend = res.data.recommend.list;
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