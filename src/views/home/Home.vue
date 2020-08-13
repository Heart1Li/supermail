<template>
  <div id="home">
    <nav-bar class="home-nav">
      <p slot="center">购物街</p>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feature-view></feature-view>
    <tab-control :tittles="['流行','新款','精选']" class="sticky" @tabClick="tabClick"></tab-control>
    <goods-list :goods="goods[currentType].list"></goods-list>
  </div>
</template>

<script>
import HomeSwiper from "views/home/childComps/HomeSwiper";
import RecommendView from "views/home/childComps/RecommendView";
import FeatureView from "views/home/childComps/FeatureView";

import NavBar from "components/common/navbar/NavBar";
import TabControl from "components/content/tabControl/TabControl";
import GoodsList from "components/content/goods/GoodsList"


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
    GoodsList,
  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods:{
        'pop' : {page:0, list:[]},
        'new' : {page:0, list:[]},
        'sell' : {page:0, list:[]},
      },
      currentType:'pop'
    };
    // result: null
  },
  created() {
    //1.请求多个数据
    this.getHomeMultidata();
    this.getHomeGoods('pop');
    this.getHomeGoods('new');
    this.getHomeGoods('sell');
    // console.log(this.goods['pop'].list)
   
  },
  methods:{
    /**
     * 事件监听方法
     */
    tabClick(index){
      console.log(index)
      switch(index){
        case 0:{
          this.currentType = 'pop'
          break
        }
        case 1:{
          this.currentType = 'new'
          break
        }
        case 2:{
          this.currentType = 'sell'
          break
        }    
      }
    },


    /**
     * 请求数据方法
     */
    getHomeMultidata(){
      getHomeMultidata().then((res) => {
      // console.log(res.data);
      this.banners = res.data.data.banner.list;
      this.recommends = res.data.data.recommend.list;
    });
    },
    getHomeGoods(type){
      // const page = this.goods[type].page + 1
       getHomeGoods(type,1).then((res) =>{
         console.log(res.data.data.list);
         //concat()方法也可以连接数组 但返回的是一个新数组
         this.goods[type].list.push(...res.data.data.list)
        //  this.goods[type].page +=1       
    })
    }
  }

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