<template>
  <div>
    <nav-bar class="home-nav"><p slot="center">购物街</p></nav-bar>
    <swiper>
      <swiper-item v-for="item in banners" :key="item.id">
        <a :href="item.link">
          <img :src="item.image" alt="">
        </a>
      </swiper-item>
    </swiper>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar';
import {getHomeMultidata} from "network/home";
// import Swiper from 'components/common/swiper/Swiper'
// import SwiperItem from 'components/common/swiper/Swiper'
import {Swiper, SwiperItem} from 'components/common/swiper/index'
export default {
  // name:'Cart'
  name:'Home',
  components:{
    NavBar,
    Swiper,
    SwiperItem,
  },
  data(){
    return{
      banners: [],
      recommends:[],
      // result: null
    }
  },
  created(){
    //1.请求多个数据
    getHomeMultidata().then(res =>{
      console.log(res.data)
      this.banners = res.data.data.banner.list;
      this.recommends = res.data.data.recommend.list;
    })
  }
}
</script>


<style scoped>
  .home-nav{
    background-color: var(--color-tint);
    color:white;
  }
</style>