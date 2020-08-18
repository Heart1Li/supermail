<template>
  <div class="wrapper" ref="wrapper" >
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  name:'Scroll',
  props: {
    pullUpLoad: {
      type: Boolean,
      default: false,
    }
  },
  data(){
    return {
      scroll:null,

    }
  },
  mounted() {
    this.scroll = new BScroll(this.$refs.wrapper,{
      click:true,
      probeType:3,
      pullUpLoad:this.pullUpLoad,
    })

    this.scroll.on('scroll',(position) =>{
      // console.log(position);
      this.$emit('scroll',position)
    })

    this.scroll.on('pullingUp', () => {
      // console.log('上拉加载')
      this.$emit('PullingUp')
    })
  }
}
</script>

<style scoped>
.wrapper {
  height: 100%;
}
</style>>

