<template>
  <div class="me">
    <h1>关于我们</h1>
    <h2>轮播图实例</h2>
    <div class="play">
      <!-- Swiper -->
      <div class="swiper-container">
        <div class="swiper-wrapper">
          <div class="swiper-slide"><img src="../../static/images/nba1.jpg" alt=""></div>
          <div class="swiper-slide"><img src="../../static/images/nba2.jpg" alt=""></div>
          <div class="swiper-slide"><img src="../../static/images/nba3.jpg" alt=""></div>
          <div class="swiper-slide"><img src="../../static/images/nba4.jpg" alt=""></div>
          <div class="swiper-slide"><img src="../../static/images/nba5.jpg" alt=""></div>
        </div>
        <div class="swiper-pagination"></div>
      </div>
    </div>
    <h2>字体图标</h2>
    <div class="ico">
      <span class="iconfont icon-camera_fill"></span>
      <span class="iconfont icon-camera"></span>
      <span class="iconfont icon-search"></span>
    </div>
  </div>
</template>

<script>
// 引入 swiper 滑动组件
import Swiper from "swiper";
import "swiper/dist/css/swiper.min.css";

export default {
  name: "Me",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },
  // 钩子函数
  mounted: function() {
    // 自己写的 js 代码  钩子函数里  
    // 调用 swiper 滑动插件的代码
    var swiper = new Swiper(".swiper-container", {
      pagination: {
        el: ".swiper-pagination",
        type: "bullets"
      }
    });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
// 引入样式表重置
@import "../assets/sass/base.scss";
// @import "../../static/css/swiper.min.css";

.me {
  h1 {
    text-align: center;
    color: aqua;
    line-height: rem(100px);
  }
  h2{
    text-align: center;
    color:blue;
    line-height: rem(100px);    
  }
}

.play {
  width: rem(750px);
  margin: 0 auto;
  .swiper-container {
    img {
      width: rem(750px);
    }
  }
}

.ico{
  span{
    font-size: rem(100px);
    color:pink;
  }
}
</style>
