<template>
  <div class="tab-control">
    <div v-for="item in tittles" :key="item.id" class="tabcontrol-item">
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
};
</script>

<style>
.tab-control {
  display: flex;
  text-align: center;
  font-size: 15px;
  background-color: white;

  border-top: 10px solid #eee;
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