<template>
  <div class="tab-control">
    <div v-for="(item,index) in tittles" :key="item.id" class="tabcontrol-item" @click="itemClick(index)">
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabControl",
  props: {
    tittles: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  data(){
    return {
      currentIndex: 0
    }
  },
  methods:{
    itemClick(index){
      this.currentIndex = index;
      this.$emit('tabClick',index)
    }
  }
};
</script>

<style>
.tab-control {
  display: flex;
  text-align: center;
  font-size: 15px;
  background-color: white;
  /* margin-top: -10px; */
  border-top: 10px solid #eee;
  z-index: 8;
}

.tabcontrol-item {
  flex: 1;
  height: 40px;
  line-height: 40px;
}
.tabcontrol-item:hover {
  color: var(--color-high-text);
}
.tabcontrol-item span:hover {
  border-bottom: 2px solid var(--color-high-text);
  padding: 0 8px;
}
.sticky {
  position: sticky;
  top: 34px;
}
</style>