<template>
  <div class="goods">
    <goods-list-item v-for="item in goods"  :goodsItem="item" :key="item.id"></goods-list-item>
    <!-- <div>{{goods}}</div> -->
  </div>
</template>

<script>
import GoodsListItem from './GoodsListItem'
export default {
  name: 'GoodList',
  props: {
    goods:{
      type: Array,
      default(){
        return []
      }
    }
  },
  components:{
    GoodsListItem,
  }
}
</script>

<style>
  .goods {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    padding: 4px;
  }
</style>