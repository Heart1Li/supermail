<template>
  <div class="recommend">
    <div v-for="item in recommends" :key="item.id" class="recommand-item">
      <a :href="item.link">
        <img :src="item.image" alt="">
        <div>{{item.title}}</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RecommendView',
  props: {
    recommends:{
      type:Array,
      default(){
        return []
      }
    }
  }
}
</script>


<style scoped>
.recommend {
  display: flex;
  text-align: center;
  padding: 15px 0 30px;
  border-bottom: 10px solid #eee;
}
.recommend-item {
  flex: 1;
  
}
.recommend img {
  width: 80%;
  height: 80%;
}
</style>