<template>
    <div class='banner' @click="changeLink">
      <mt-swipe :auto="4000" :speed="500" >
        <mt-swipe-item v-for="item in banners" 
        :style="{background:'url('+item.pic+') center center no-repeat'}" :data-link="item.link">
        </mt-swipe-item>
      </mt-swipe>
    </div>
</template>

<script>
import { Swipe, SwipeItem } from 'mint-ui';

export default {
  name: 'HelloWorld',
  data () {
    return {
      banners: [
        {
          pic: 'http://www.guocheng54.com/newblog/images/banner/banner1.jpg',
          link: '/about'   //跳转到对应的页面
        },
        {
          pic: 'http://www.guocheng54.com/newblog/images/banner/banner2.jpg',
          link: 'www.imooc.com'
        },
        {
          pic: 'http://www.guocheng54.com/newblog/images/banner/banner3.jpg',
          link: 'www.linguocheng54.com/newblog'
        },
      ]
    }
  },
  components: {
    [Swipe.name]: Swipe,
    [SwipeItem.name]: SwipeItem
  },
  methods: {
    changeLink (e) {
      let link = e.target.dataset['link'];
      this.$router.push(link)

    }
  }
}
</script> 

<style lang="less">
.banner {
  height: 200px;
}
.mint-swipe-item {
  background-size: 100% 100% !important;
}
</style>
