<template>
  <div>
    <div id='header'>
      <div class='logo' v-if='logoshow'>NewBlog</div>
      <!--返回上一页-->
      <div class='back-btn' v-else @click='$router.go(-1)'>
        &lt;
      </div>

      <!--打开导航栏按钮-->
      <div class='nav-btn' @click='shownav' v-if="!flag">
          <span></span>
          <span></span>
          <span></span>
      </div>
      <!--关闭导航栏按钮-->
      <div class='nav-closebtn' @click='shownav' v-else>
        <span :class='{close:trueclose}'></span>
        <span :class='{close:trueclose}'></span>
      </div>
    </div>
    <!--导航栏-->
    <div class="nav" ref='nav'>
      <ul>
        <li><a href='#'>首页</a></li>
        <li><a href='#'>技术文档</a></li>
        <li><a href='#'>阅读笔记</a></li>
        <li><a href='#'>关于我</a></li>
        <li><a href='#'>前端导航</a></li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      flag: false,
      trueclose: false
    }
  },
  props: {
    logoshow: {
      type: Boolean,
      default: true
    }
  },
  methods: {
    shownav(){
      let nav = this.$refs.nav;
      if(!this.flag){
         //点击之后，改变nav的显示与隐藏，并且有过渡效果
        nav.style.height = '190px';
        //为了动画
        setTimeout(() => {
          this.trueclose = true;
        },0)
        
        this.flag = !this.flag;

      }else {
        nav.style.height = '0px';
        this.trueclose = false;
        this.flag = !this.flag;
      }
    },
    //返回上一页
    // backpage(){
      // this.$router.go(-1)
    // }
  }
}
</script>>
<style lang="less" scoped>
  #header {
    width: 100%;
    height: 60px;
    line-height: 60px;
    background: hsla(250, 100%, 60%, 1);
    padding: 0 10px;
    box-sizing: border-box;
    .back-btn {
      float: left;
      width: 40px;
      height: 100%;
      text-align: center;
      font-size: 36px;
      color: #fff;
    }
    .logo {
      float: left;
      height: 100%;
      font-size: 16px;
      font-weight: bold;
      color: #fff;
    }
    .nav-btn {
      float: right;
      width: 60px;
      height: 100%;
      box-sizing: border-box;
      padding: 10px;
      text-align: center;
      span {
        display: block;
        height: 2px;
        background: #fff;
        width: 100%;
        margin-top: 10px;
      }
      
    }
    .nav-closebtn {
        float: right;
        width: 60px;
        height: 100%;
        box-sizing: border-box;
        padding: 10px;
        text-align: center;
        position: relative;
        span {
          display:block;
          width: 40px;
          background: #fff;
          height: 2px;
          position:absolute;
          left:0;
          top: 0;
          bottom: 0;
          right: 0;
          margin: auto;
          transform: rotateZ(0deg);
          transition: transform .5s;
        }
        .close:first-child {
          transform: rotateZ(45deg);
        }
        .close:last-child {
          transform: rotateZ(-45deg);
        }
      }
    
    &::after {
      display: block;
      height: 0;
      content: '';
      visibility: hidden;
      clear: both;
    }
  }
  .nav {
    background:hsla(250, 100%, 60%, 1);
    margin-top: 2px;
    overflow: hidden;
    transition: height .5s;
    height: 0;
    ul {
      padding: 20px 0;
      li {
        height: 30px;
        line-height: 30px;
        a {
          color: #fff;
        }
      }
    }
  }
</style>