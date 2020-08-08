<template>
  <TabBar>
      <TabBarItem path="/home" activeColor="deepPink">
        <img slot="item-icon" src="~assets/img/tabbar/home.svg" alt=""/>
        <img slot="item-icon-active" src="~assets/img/tabbar/home_active.svg" alt=""/>
        <p slot="item-text">首页</p>
      </TabBarItem>
      <TabBarItem path="/category" activeColor="deepPink">
        <img slot="item-icon" src="~assets/img/tabbar/category.svg" alt=""/>
        <img slot="item-icon-active" src="~assets/img/tabbar/category_active.svg" alt=""/>
        <p slot="item-text">分类</p>
      </TabBarItem>
      <TabBarItem path="/cart" activeColor="deepPink">
        <img slot="item-icon" src="~assets/img/tabbar/cart.svg" alt=""/>
        <img slot="item-icon-active" src="~assets/img/tabbar/cart_active.svg" alt=""/>
        <p slot="item-text">购物车</p>
      </TabBarItem>
      <TabBarItem path="/profile" activeColor="deepPink">
        <img slot="item-icon" src="~assets/img/tabbar/profile.svg" alt=""/>
        <img slot="item-icon-active" src="~assets/img/tabbar/profile_active.svg" alt=""/>
        <p slot="item-text">我的</p>
      </TabBarItem>
    </TabBar>
</template>

<script>
import TabBar from "common/tabbar/TabBar";
import TabBarItem from "common/tabbar/TabBarItem";
export default {
  name:'MainTabBar',
  components: {
    TabBar,
    TabBarItem,
  },
}
</script>

<style scoped>

</style>