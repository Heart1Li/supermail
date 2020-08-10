<template>
  <div id="home">
    <nav-bar class="home-nav">
      <p slot="center">购物街</p>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feature-view></feature-view>
    <tab-control :tittles="['流行','新款','精选']" class="sticky"></tab-control>

    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
    <ul><li>123</li></ul>
  </div>
</template>

<script>
import HomeSwiper from "views/home/childComps/HomeSwiper";
import RecommendView from "views/home/childComps/RecommendView";
import FeatureView from "views/home/childComps/FeatureView";

import NavBar from "components/common/navbar/NavBar";
import TabControl from "components/content/tabControl/TabControl";


import { getHomeMultidata,getHomeGoods, } from "network/home";
// import Swiper from 'components/common/swiper/Swiper'
// import SwiperItem from 'components/common/swiper/Swiper'

export default {
  // name:'Cart'
  name: "Home",
  components: {
    NavBar,
    TabControl,
    HomeSwiper,
    RecommendView,
    FeatureView,
  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods:{
        'pop' : {page:0,list:[]},
        'news' : {page:0,list:[]},
        'sell' : {page:0,list:[]},
      }
    };
    // result: null
  },
  created() {
    //1.请求多个数据
    getHomeMultidata().then((res) => {
      console.log(res.data);
      this.banners = res.data.data.banner.list;
      this.recommends = res.data.data.recommend.list;
    });

    getHomeGoods().then((res) =>{
      console.log(res.data);
    })
  },

};
</script>


<style scoped>
#home {
  padding-top: 44px;
}
.home-nav {
  background-color: var(--color-tint);
  color: white;

  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
}
</style>